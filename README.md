<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cole Frank | Premium Banking</title>

<style>
/* ==========================
   COLOR THEME + VARIABLES
========================== */
:root {
    --red: #b30000;
    --red-light: #d32f2f;
    --gold: #ffd54f;
    --gold-bright: #ffeb3b;
    --purple: #7e57c2;
    --blue: #1976d2;
    --teal: #26a69a;

    --light-bg: #f5f5f8;
    --dark-bg: #121212;
    --card-light: rgba(255,255,255,0.82);
    --card-dark: rgba(40,40,40,0.75);
    --text-light: #000;
    --text-dark: #fff;
}

/* Animated Color Background */
body {
    margin: 0;
    font-family: "Inter", sans-serif;
    background: linear-gradient(135deg, var(--red), var(--purple), var(--blue));
    background-size: 400% 400%;
    animation: bgShift 15s ease infinite;
    transition: 0.4s;
    color: var(--text-light);
}

@keyframes bgShift {
    0% {background-position: 0% 50%;}
    50% {background-position: 100% 50%;}
    100% {background-position: 0% 50%;}
}

/* Dark Mode */
body.dark {
    background: linear-gradient(135deg, #000, #111, #222);
    color: var(--text-dark);
}

/* Floating shapes behind */
.shape {
    position: fixed;
    width: 200px;
    height: 200px;
    border-radius: 50%;
    filter: blur(70px);
    opacity: 0.55;
    animation: float 20s infinite alternate ease-in-out;
    z-index: -1;
}

@keyframes float {
    from {transform: translateY(0px);}
    to {transform: translateY(-60px);}
}

.shape.red {background: var(--red-light); top: 10%; left: 10%;}
.shape.gold {background: var(--gold); top: 70%; left: 60%;}
.shape.blue {background: var(--blue); top: 30%; left: 70%;}

/* Login Box */
.centered {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    padding: 20px;
}

.card {
    background: var(--card-light);
    padding: 40px;
    width: 380px;
    border-radius: 25px;
    backdrop-filter: blur(25px);
    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
    animation: fadeInUp 0.9s ease;
    text-align: center;
}

body.dark .card {
    background: var(--card-dark);
}

/* Animations */
@keyframes fadeInUp {
    from {opacity: 0; transform: translateY(30px);}
    to {opacity: 1; transform: translateY(0);}
}

input {
    width: 100%;
    padding: 14px;
    margin-top: 15px;
    border-radius: 12px;
    border: none;
    font-size: 16px;
    outline: none;
}

button {
    width: 100%;
    margin-top: 22px;
    padding: 14px;
    border-radius: 14px;
    border: none;
    background: linear-gradient(135deg, var(--gold), var(--gold-bright));
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
    color: #000;
    transition: 0.4s;
    box-shadow: 0 8px 18px rgba(0,0,0,0.25);
}

button:hover {
    transform: scale(1.03);
    box-shadow: 0 12px 25px rgba(0,0,0,0.35);
}

/* Dashboard */
#dashboard {
    display: none;
    padding: 40px;
}

/* Header */
.header {
    display: flex;
    justify-content: space-between;
    padding: 20px 40px;
    background: rgba(255,255,255,0.12);
    color: #fff;
    font-size: 22px;
    font-weight: 600;
    backdrop-filter: blur(20px);
    border-bottom: 1px solid rgba(255,255,255,0.2);
}

/* Dark Mode Toggle */
.toggle {
    cursor: pointer;
    padding: 8px 16px;
    border-radius: 12px;
    background: var(--gold);
    color: #000;
    font-weight: bold;
}

/* Balance Card */
.balance-card {
    margin: 25px auto;
    background: linear-gradient(135deg, var(--red), var(--gold));
    padding: 30px;
    border-radius: 22px;
    width: 350px;
    box-shadow: 0 20px 40px rgba(0,0,0,0.3);
    color: #fff;
    text-align: center;
}

/* Dashboard Sections */
.section {
    background: var(--card-light);
    padding: 22px;
    border-radius: 20px;
    width: 350px;
    margin: 20px auto;
    backdrop-filter: blur(12px);
}

body.dark .section {
    background: var(--card-dark);
}

.section h3 {
    margin-top: 0;
    margin-bottom: 10px;
}
</style>
</head>

<body>

<div class="shape red"></div>
<div class="shape gold"></div>
<div class="shape blue"></div>

<!-- LOGIN -->
<div id="login-section" class="centered">
    <div class="card">
        <h2 style="margin-bottom:10px;">Apex Credit Union Login</h2>
        <p style="margin-top:0;">Secure Access</p>
        <input id="username" placeholder="Username">
        <input id="password" type="password" placeholder="Password">
        <button onclick="login()">Login</button>
        <p id="error" style="color:#ffdddd; display:none; margin-top:10px;">❗ Incorrect login details</p>
    </div>
</div>

<!-- DASHBOARD -->
<div id="dashboard">
    <div class="header">
        <div>Welcome, <span id="name"></span></div>
        <div class="toggle" onclick="toggleDark()">Dark Mode</div>
    </div>

    <div class="balance-card">
        <h2>Current Account</h2>
        <h1 id="balance"></h1>
        <p>Last Transaction Date: <span id="lastTxn"></span></p>
    </div>

    <div class="section">
        <h3>Recent Transactions</h3>
        <ul style="line-height: 1.8;">
            <li> account restricted !</li>
        </ul>
    </div>

    <div class="section">
        <h3>Send Money</h3>
        <input placeholder="Recipient Name" />
        <input placeholder="Amount (USD)" />
        <button>Send</button>
    </div>

    <div class="section">
        <h3>Your Cards</h3>
        <p>💳 Visa Debit •••• 1124</p>
        <p>💳 Mastercard •••• 8899</p>
    </div>
</div>

<script>
const correctUser = "Colefrank444";
const correctPass = "Frank2017";

function login() {
    const u = document.getElementById("username").value;
    const p = document.getElementById("password").value;

    if (u === correctUser && p === correctPass) {
        document.getElementById("login-section").style.display = "none";
        document.getElementById("dashboard").style.display = "block";

        document.getElementById("name").innerText = "Cole Frank";
        document.getElementById("balance").innerText = "$15,312.87";
        document.getElementById("lastTxn").innerText = "March 18, 2025";
    } else {
        document.getElementById("error").style.display = "block";
    }
}

function toggleDark() {
    document.body.classList.toggle("dark");
}
</script>

</body>
</html>
