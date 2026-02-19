<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cyber Security Password Strength Checker</title>

<style>
/* Animated Background */
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(-45deg, #0f2027, #203a43, #2c5364, #1f1c2c);
    background-size: 400% 400%;
    animation: gradientBG 10s ease infinite;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    color: white;
}

@keyframes gradientBG {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
}

/* Glass Card */
.container {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    padding: 30px;
    border-radius: 15px;
    width: 400px;
    box-shadow: 0 0 20px rgba(0,0,0,0.5);
}

h2 {
    text-align: center;
    margin-bottom: 10px;
}

input {
    width: 100%;
    padding: 12px;
    margin-top: 10px;
    font-size: 16px;
    border: none;
    border-radius: 5px;
}

button {
    margin-top: 10px;
    padding: 8px 15px;
    border: none;
    border-radius: 5px;
    background: #00c6ff;
    color: white;
    cursor: pointer;
}

.progress {
    height: 10px;
    background: rgba(255,255,255,0.3);
    border-radius: 5px;
    margin-top: 15px;
}

.progress-bar {
    height: 10px;
    width: 0%;
    border-radius: 5px;
    transition: 0.4s;
}

ul {
    margin-top: 15px;
    padding-left: 20px;
    font-size: 14px;
}

li {
    margin-bottom: 5px;
}

.info {
    margin-top: 20px;
    font-size: 13px;
    line-height: 1.4;
    background: rgba(0,0,0,0.3);
    padding: 10px;
    border-radius: 8px;
}

.weak { background: red; }
.medium { background: orange; }
.strong { background: limegreen; }

.footer {
    text-align: center;
    font-size: 12px;
    margin-top: 10px;
    opacity: 0.7;
}
</style>
</head>

<body>

<div class="container">
    <h2>🔐 Cyber Security Password Checker</h2>

    <input type="password" id="password" placeholder="Enter Secure Password" onkeyup="checkPassword()">
    <button onclick="togglePassword()">Show / Hide</button>

    <div class="progress">
        <div class="progress-bar" id="progressBar"></div>
    </div>

    <ul>
        <li id="length">✔ Minimum 8 characters</li>
        <li id="upper">✔ At least 1 Uppercase letter</li>
        <li id="number">✔ At least 1 Number</li>
        <li id="special">✔ Special Character (@$!%*?&)</li>
    </ul>

    <div class="info">
        <b>About Cyber Security:</b><br>
        Cyber security is the practice of protecting systems, networks,
        and data from digital attacks. Strong passwords prevent hacking,
        data theft, identity fraud, and unauthorized access.
        Always use a complex password and never share it with anyone.
    </div>

    <div class="footer">
        Designed for Cyber Awareness Project
    </div>
</div>

<script>
function checkPassword() {
    var password = document.getElementById("password").value;
    var strength = 0;

    var length = document.getElementById("length");
    var upper = document.getElementById("upper");
    var number = document.getElementById("number");
    var special = document.getElementById("special");
    var progressBar = document.getElementById("progressBar");

    if (password.length >= 8) {
        strength++;
        length.style.color = "lime";
    } else { length.style.color = "red"; }

    if (password.match(/[A-Z]/)) {
        strength++;
        upper.style.color = "lime";
    } else { upper.style.color = "red"; }

    if (password.match(/[0-9]/)) {
        strength++;
        number.style.color = "lime";
    } else { number.style.color = "red"; }

    if (password.match(/[@$!%*?&]/)) {
        strength++;
        special.style.color = "lime";
    } else { special.style.color = "red"; }

    if (strength == 1) {
        progressBar.style.width = "25%";
        progressBar.className = "progress-bar weak";
    } 
    else if (strength == 2 || strength == 3) {
        progressBar.style.width = "60%";
        progressBar.className = "progress-bar medium";
    } 
    else if (strength == 4) {
        progressBar.style.width = "100%";
        progressBar.className = "progress-bar strong";
    } 
    else {
        progressBar.style.width = "0%";
    }
}

function togglePassword() {
    var pass = document.getElementById("password");
    pass.type = (pass.type === "password") ? "text" : "password";
}
</script>

</body>
</html>
