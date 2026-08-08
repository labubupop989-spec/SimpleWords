<!DOCTYPE html>
<html lang="ro">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistem Autentificare & Admin</title>
    <style>
        /* Stiluri Generale */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f0f2f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        /* Ecranul de Login */
        .login-container {
            background: #ffffff;
            padding: 40px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 400px;
        }

        .login-container h2 {
            margin-bottom: 24px;
            color: #333;
            text-align: center;
        }

        .input-group {
            margin-bottom: 20px;
        }

        .input-group label {
            display: block;
            margin-bottom: 8px;
            color: #666;
            font-size: 14px;
        }

        .input-group input {
            width: 100%;
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 16px;
        }

        .input-group input:focus {
            border-color: #0066cc;
            outline: none;
        }

        .btn-login {
            width: 100%;
            padding: 12px;
            background-color: #0066cc;
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 16px;
            cursor: pointer;
            font-weight: bold;
        }

        .btn-login:hover {
            background-color: #0052a3;
        }

        .error-message {
            color: #ff3333;
            font-size: 14px;
            margin-top: 12px;
            text-align: center;
            display: none;
        }

        /* Panoul de Admin (Ascuns inițial) */
        .admin-container {
            display: none;
            width: 90%;
            max-width: 1200px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            height: 80vh;
        }

        .admin-sidebar {
            width: 250px;
            background: #2c3e50;
            color: white;
            padding: 20px;
            float: left;
            height: 100%;
        }

        .admin-sidebar h3 {
            margin-bottom: 30px;
            padding-bottom: 10px;
            border-bottom: 1px solid #34495e;
        }

        .admin-sidebar ul {
            list-style: none;
        }

        .admin-sidebar ul li {
            padding: 12px;
            cursor: pointer;
            border-radius: 4px;
            margin-bottom: 8px;
        }

        .admin-sidebar ul li:hover, .admin-sidebar ul li.active {
            background: #34495e;
        }

        .btn-logout {
            background: #e74c3c;
            color: white;
            border: none;
            padding: 10px;
            width: 100%;
            border-radius: 4px;
            cursor: pointer;
            margin-top: 50px;
        }

        .admin-main {
            margin-left: 250px;
            padding: 40px;
            background: #fafafa;
            height: 100%;
            overflow-y: auto;
        }

        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: white;
            padding: 20px;
            border-radius: 6px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
            border-left: 4px solid #0066cc;
        }

        .stat-card h4 {
            color: #888;
            font-size: 14px;
            margin-bottom: 10px;
        }

        .stat-card p {
            font-size: 24px;
            font-weight: bold;
            color: #333;
        }

        /* Tabel Admin */
        table {
            width: 100%;
            border-collapse: collapse;
            background: white;
            border-radius: 6px;
            overflow: hidden;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }

        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid #eee;
        }

        th {
            background-color: #f4f6f9;
            color: #666;
        }
    </style>
</head>
<body>

    <!-- SECȚIUNEA 1: ECRANUL DE LOGIN -->
    <div class="login-container" id="loginBox">
        <h2>Autentificare</h2>
        <div class="input-group">
            <label for="username">Utilizator (Folosește: admin)</label>
            <input type="text" id="username" placeholder="Introdu utilizatorul">
        </div>
        <div class="input-group">
            <label for="password">Parolă (Folosește: admin123)</label>
            <input type="password" id="password" placeholder="Introdu parola">
        </div>
        <button class="btn-login" onclick="checkLogin()">Conectare</button>
        <div class="error-message" id="errorMsg">Utilizator sau parolă incorectă!</div>
    </div>

    <!-- SECȚIUNEA 2: PANOUL DE ADMINISTRARE -->
    <div class="admin-container" id="adminPanel">
        <!-- Meniu Lateral -->
        <div class="admin-sidebar">
            <h3>Admin Panel</h3>
            <ul>
                <li class="active">Dashboard</li>
                <li>Utilizatori</li>
                <li>Setări</li>
            </ul>
            <button class="btn-logout" onclick="logout()">Deconectare</button>
        </div>

        <!-- Conținut Principal -->
        <div class="admin-main">
            <div class="admin-header">
                <h2>Panou de Control</h2>
                <span>Bine ai venit, <strong>Admin</strong>!</span>
            </div>

            <!-- Carduri Statistici -->
            <div class="stats-grid">
                <div class="stat-card">
                    <h4>Utilizatori Noi</h4>
                    <p>1,245</p>
                </div>
                <div class="stat-card" style="border-left-color: #2ecc71;">
                    <h4>Vânzări Lunare</h4>
                    <p>€14,230</p>
                </div>
                <div class="stat-card" style="border-left-color: #e67e22;">
                    <h4>Trafic Site</h4>
                    <p>45,800</p>
                </div>
            </div>

            <!-- Tabel Date -->
            <h3>Utilizatori Recenți</h3>
            <table>
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>Nume</th>
                        <th>Email</th>
                        <th>Status</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>#1024</td>
                        <td>Ion Popescu</td>
                        <td>ion.popescu@email.com</td>
                        <td style="color: #2ecc71; font-weight: bold;">Activ</td>
                    </tr>
                    <tr>
                        <td>#1023</td>
                        <td>Elena Radu</td>
                        <td>elena.radu@email.com</td>
                        <td style="color: #2ecc71; font-weight: bold;">Activ</td>
                    </tr>
                    <tr>
                        <td>#1022</td>
                        <td>Andrei Nistor</td>
                        <td>andrei.n@email.com</td>
                        <td style="color: #e74c3c; font-weight: bold;">Inactiv</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>

    <!-- SCRIPT LOGICĂ (Simulare Autentificare) -->
    <script>
        function checkLogin() {
            var user = document.getElementById("username").value;
            var pass = document.getElementById("password").value;
            var error = document.getElementById("errorMsg");
            var loginBox = document.getElementById("loginBox");
            var adminPanel = document.getElementById("adminPanel");

            // Date de test obligatorii
            if (user === "admin" && pass === "admin123") {
                error.style.display = "none";
                loginBox.style.display = "none"; // Ascunde login
                adminPanel.style.display = "block"; // Arată admin
            } else {
                error.style.display = "block"; // Arată eroare
            }
        }

        function logout() {
            document.getElementById("username").value = "";
            document.getElementById("password").value = "";
            document.getElementById("adminPanel").style.display = "none"; // Ascunde admin
            document.getElementById("loginBox").style.display = "block"; // Arată login
        }
    </script>

</body>
</html>
