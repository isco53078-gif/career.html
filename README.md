<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Career Unlocker | IscoTech</title>
    <style>
        :root { --navy: #000814; --gold: #ffc300; --mpesa: #28a745; }
        body { font-family: 'Segoe UI', sans-serif; background: #f4f7f6; margin: 0; }
        .header { background: var(--navy); color: white; padding: 40px 20px; text-align: center; border-bottom: 5px solid var(--gold); }
        .card { background: white; max-width: 450px; margin: -30px auto 20px; padding: 30px; border-radius: 20px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); text-align: center; }
        input, select { width: 100%; padding: 15px; margin: 10px 0; border: 2px solid #ddd; border-radius: 12px; font-size: 16px; box-sizing: border-box; }
        .btn { width: 100%; padding: 18px; border: none; border-radius: 50px; font-weight: 800; cursor: pointer; font-size: 1.1em; }
        #paySection { display: none; }
        .loader { border: 4px solid #f3f3f3; border-top: 4px solid var(--mpesa); border-radius: 50%; width: 30px; height: 30px; animation: spin 1s linear infinite; display: none; margin: 10px auto; }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
    </style>
</head>
<body>

<div class="header">
    <h1>IscoTech Career AI</h1>
    <p>Premium Placement System 2026</p>
</div>

<div class="container" style="padding: 0 15px;">
    <div class="card" id="inputSection">
        <h3>1. Enter Results</h3>
        <input type="text" id="name" placeholder="Full Student Name">
        <select id="grade">
            <option value="">Select Mean Grade</option>
            <option value="Degree">C+ to A</option>
            <option value="Diploma">C to C-</option>
            <option value="Cert">D+ to D</option>
            <option value="Artisan">E</option>
        </select>
        <button class="btn" style="background:var(--navy); color:white;" onclick="toPay()">Generate Report</button>
    </div>

    <div class="card" id="paySection">
        <h3 style="color:var(--mpesa)">🔒 Report Locked</h3>
        <p>A fee of <b>100/-</b> is required to unlock the results for <b id="uName"></b>.</p>
        
        <div style="background:#f0fff4; border:2px dashed var(--mpesa); padding:15px; border-radius:15px; margin:15px 0;">
            <p style="margin:0;">Send 100/- to M-PESA:<br>
            <b style="font-size:1.4em;">0746939408</b></p>
        </div>

        <input type="text" id="mCode" placeholder="Paste M-PESA Message Here" required>
        <div id="loading" class="loader"></div>
        <button class="btn" style="background:var(--mpesa); color:white;" onclick="verify()">Verify & Unlock Results</button>
    </div>
</div>

<script>
    function toPay() {
        const name = document.getElementById('name').value;
        const grade = document.getElementById('grade').value;
        if(!name || !grade) { alert("Please enter your details!"); return; }
        
        document.getElementById('uName').innerText = name;
        document.getElementById('inputSection').style.display = "none";
        document.getElementById('paySection').style.display = "block";
    }

    function verify() {
        const code = document.getElementById('mCode').value;
        if(code.length < 10) {
            alert("Please paste the FULL M-PESA message to verify payment.");
            return;
        }

        document.getElementById('loading').style.display = "block";
        
        // Simulating a check...
        setTimeout(() => {
            const name = document.getElementById('name').value;
            const grade = document.getElementById('grade').value;
            const mpesa = document.getElementById('mCode').value;
            
            // This sends the data to YOU. You are the "Automatic System" for now.
            const text = `VERIFICATION REQUEST%0A---%0AName: ${name}%0AGrade: ${grade}%0AM-PESA: ${mpesa}`;
            window.location.href = `https://wa.me/254746939408?text=${text}`;
        }, 2000);
    }
</script>

</body>
</html>
