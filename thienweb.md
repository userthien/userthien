<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trang Web Cá Nhân</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            text-align: center;
            padding: 50px;
        }
        .hidden {
            display: none;
        }
        .login-form, .profile {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            display: inline-block;
        }
        .login-form input {
            margin: 10px 0;
            padding: 10px;
            width: 100%;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        .profile h2 {
            color: #007BFF;
        }
		 #ipAddress {
            color: #ff0000; 
		
		</style>
</head>
<body>

<div class="login-form" id="loginForm">
    <h2>Đăng Nhập</h2>
    <input type="password" id="password" placeholder="Nhập mật khẩu">
    <button onclick="login()">Đăng Nhập</button>
    <p id="errorMessage" style="color: red;"></p>
</div>

<div class="profile hidden" id="profile">
    <h2>Thông Tin Cá Nhân</h2>
    <p id="ipAddress">Địa chỉ IP của bạn là: <span id="ip"></span></p>
    <p>Xin chào, tôi là Thiên. Đây là trang web cá nhân của tôi. Vui lòng nhập mật khẩu 'ipcuatoi' để kiểm tra IP của bạn.</p>
<div class="social-link">
     <a href="https://www.facebook.com/toikhongtontai09" target="_blank">Facebook</a>
</div>
</div>


<script>
    const correctPassword = 'ipcuatoi';

    function login() {
        const passwordInput = document.getElementById('password').value;
        const errorMessage = document.getElementById('errorMessage');
        const loginForm = document.getElementById('loginForm');
        const profile = document.getElementById('profile');

        if (passwordInput === correctPassword) {
            loginForm.classList.add('hidden');
            profile.classList.remove('hidden');
            fetchIpAddress();
        } else {
            errorMessage.textContent = 'Mật khẩu không chính xác. Vui lòng thử lại.';
        }
    }

    function fetchIpAddress() {
        fetch('https://api.ipify.org?format=json')
            .then(response => response.json())
            .then(data => {
                document.getElementById('ip').textContent = data.ip;
            })
            .catch(error => {
                console.error('Có lỗi xảy ra khi lấy địa chỉ IP:', error);
                document.getElementById('ip').textContent = 'Không thể lấy địa chỉ IP';
			 });
     }
</script>

</body>
</html>	 
