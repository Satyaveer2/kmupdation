<!DOCTYPE html>
<html>
<head>
    <title>Login - YOTS</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- Font Awesome for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
    <style>
        html, body {
            height: 100%;
            margin: 0;
            padding: 0;
        }
        body {
            min-height: 100vh;
            min-width: 100vw;
            font-family: 'Segoe UI', Arial, sans-serif;
            background: url('https://pplx-res.cloudinary.com/image/upload/v1747519500/user_uploads/65050862/e370359e-6b2f-46ae-a500-9dc93d2d0ee6/1000006174.jpg') no-repeat center center fixed;
            background-size: cover;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
        }
        /* Watermark YOTS */
        .watermark-yots {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 8vw;
            font-weight: bold;
            color: #1e88e5;
            opacity: 0.11;
            pointer-events: none;
            user-select: none;
            letter-spacing: 16px;
            white-space: nowrap;
            z-index: 1;
            text-shadow: 0 2px 8px #fff, 0 0 2px #fff;
        }
        .login-box {
            position: relative;
            z-index: 2;
            background: rgba(255,255,255,0.97);
            padding: 30px 30px 24px 30px;
            border-radius: 10px;
            box-shadow: 0 4px 20px 0 rgba(31,38,135,0.13);
            width: 350px;
            max-width: 95vw;
            text-align: left;
            display: flex;
            flex-direction: column;
            align-items: stretch;
        }
        .login-title {
            font-size: 1.3em;
            color: #b71c1c;
            font-weight: bold;
            margin-bottom: 18px;
            letter-spacing: 1px;
            text-align: center;
        }
        .input-group {
            position: relative;
            margin-bottom: 16px;
        }
        .input-group input {
            width: 100%;
            padding: 10px 12px 10px 38px;
            border: 1px solid #bdbdbd;
            border-radius: 5px;
            font-size: 1em;
            background: #fafafa;
            box-sizing: border-box;
            outline: none;
        }
        .input-group .fa-solid {
            position: absolute;
            left: 12px;
            top: 50%;
            transform: translateY(-50%);
            color: #1e88e5;
            font-size: 1.08em;
        }
        .remember-row {
            display: flex;
            align-items: center;
            margin-bottom: 16px;
            font-size: 0.98em;
        }
        .remember-row input[type="checkbox"] {
            margin-right: 7px;
        }
        .sign-in-btn {
            width: 100%;
            padding: 11px 0;
            background: #29aafc;
            color: #fff;
            border: none;
            border-radius: 5px;
            font-size: 1.09em;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.2s;
            margin-top: 2px;
        }
        .sign-in-btn:hover {
            background: #1e88e5;
        }
        #error {
            color: #e53935;
            margin-top: 10px;
            min-height: 20px;
            font-size: 0.97em;
            text-align: center;
        }
        @media (max-width: 600px) {
            .watermark-yots {
                font-size: 13vw;
                letter-spacing: 7px;
            }
            .login-box {
                width: 95vw;
                padding: 14px 6vw 12px 6vw;
            }
        }
    </style>
</head>
<body>
    <div class="watermark-yots">YOTS</div>
    <div class="login-box">
        <div class="login-title">Login</div>
        <form onsubmit="login(event)">
            <div class="input-group">
                <i class="fa-solid fa-user"></i>
                <input type="text" id="username" placeholder="Username" autocomplete="username" required>
            </div>
            <div class="input-group">
                <i class="fa-solid fa-lock"></i>
                <input type="password" id="password" placeholder="Password" autocomplete="current-password" required>
            </div>
            <div class="remember-row">
                <input type="checkbox" id="rememberMe">
                <label for="rememberMe" style="margin:0; font-weight:400;">Remember me</label>
            </div>
            <button type="submit" class="sign-in-btn">Sign In</button>
            <div id="error"></div>
        </form>
    </div>
    <script>
        // Optional: Remember Me functionality using localStorage
        window.onload = function() {
            if(localStorage.getItem("rememberUser")) {
                document.getElementById("username").value = localStorage.getItem("rememberUser");
                document.getElementById("rememberMe").checked = true;
            }
        }
        function login(e) {
            e.preventDefault();
            const user = document.getElementById("username").value;
            const pass = document.getElementById("password").value;
            const remember = document.getElementById("rememberMe").checked;
            if (user === "youngip" && pass === "cluster2") {
                if(remember) {
                    localStorage.setItem("rememberUser", user);
                } else {
                    localStorage.removeItem("rememberUser");
                }
                sessionStorage.setItem("loggedIn", "true");
                window.location.href = "dashboard.html";
            } else {
                document.getElementById("error").innerText = "Invalid credentials";
            }
        }
    </script>
</body>
</html>
