<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Career Analyzer | IscoTech Academy</title>
    <style>
        :root { --navy: #000814; --gold: #ffc300; --mpesa: #28a745; }
        body { font-family: 'Segoe UI', sans-serif; background: #f0f2f5; margin: 0; }
        .header { background: var(--navy); color: white; padding: 40px 15px; text-align: center; border-bottom: 5px solid var(--gold); }
        .container { max-width: 600px; margin: -30px auto 50px; padding: 0 15px; }
        .card { background: white; padding: 25px; border-radius: 20px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); }
        
        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; margin-top: 10px; }
        h4 { margin: 20px 0 10px 0; color: var(--navy); border-bottom: 2px solid var(--gold); display: inline-block; }
        input, select { width: 100%; padding: 12px; margin: 5px 0; border: 1px solid #ccc; border-radius: 8px; box-sizing: border-box; }
        
        .btn { width: 100%; padding: 18px; border: none; border-radius: 50px; font-weight: 800; cursor: pointer; font-size: 1.1em; margin-top: 25px; }
        #paymentGate { display: none; text-align: center; }
        .mpesa-card { background: #f0fff4; border: 2px dashed var(--mpesa); padding: 20px; border-radius: 15px; margin: 20px 0; }
    </style>
</head>
<body>

<div class="header">
    <h1>IscoTech Career AI</h1>
    <p>Professional KCSE Grade Analysis & Placement</p>
</div>

<div class="container">
    <div class="card" id="formScreen">
        <h3>1. Student Bio</h3>
        <input type="text" id="name" placeholder="Full Name">
        <input type="text" id="index" placeholder="Index Number (11 Digits)">
        
        <h4>2. Core Subjects</h4>
        <div class="grid">
            <div><label>Maths</label><select id="mth"><option>A</option><option>A-</option><option>B+</option><option>B</option><option>B-</option><option>C+</option><option>C</option><option>C-</option><option>D+</option><option>D</option><option>D-</option><option>E</option></select></div>
            <div><label>English</label><select id="eng"><option>A</option><option>A-</option><option>B+</option><option>B</option><option>B-</option><option>C+</option><option>C</option><option>C-</option><option>D+</option><option>D</option><option>D-</option><option>E</option></select></div>
            <div><label>Kiswahili</label><select id="kis"><option>A</option><option>A-</option><option>B+</option><option>B</option><option>B-</option><option>C+</option><option>C</option><option>C-</option><option>D+</option><option>D</option><option>D-</option><option>E</option></select></div>
            <div><label>MEAN GRADE</label><select id="mean" style="background:#fff9c4; font-weight:bold;"><option>A</option><option>A-</option><option>B+</option><option>B</option><option>B-</option><option>C+</option><option>C</option><option>C-</option><option>D+</option><option>D</option><option>D-</option><option>E</option></select></div>
        </div>

        <h4>3. Sciences & Electives</h4>
        <div class="grid">
            <input type="text" id="bio" placeholder="Biology Grade">
            <input type="text" id="chem" placeholder="Chem/Physics Grade">
            <input type="text" id="hist" placeholder="History/Geo Grade">
            <input type="text" id="cre" placeholder="CRE/IRE Grade">
            <input type="text" id="agri" placeholder="Agri/Business Grade">
            <input type="text" id="other" placeholder="Subject 8 (Optional)">
        </div>

        <button class="btn" style="background:var(--navy); color:white;" onclick="toPayment()">Analyze My Future</button>
    </div>

    <div class="card" id="paymentGate">
        <h3 style="color:#d32f2f;">🔒 PLACEMENT ANALYSIS LOCKED</h3>
        <p>Comprehensive career mapping for <b><span id="displayUser"></span></b> has been generated based on the provided 8 subjects.</p>
        
        <div class="mpesa-card">
            <p>To unlock the Report & University List, pay <b>100/-</b> to:<br>
            <b style="font-size:1.5em; color:var(--mpesa);">0746939408</b><br>
            (ISCOTECH ACADEMY)</p>
        </div>

        <input type="text" id="mpesaCode" placeholder="Paste M-PESA Confirmation Code Here">
        <button class="btn" style="background:var(--mpesa); color:white;" onclick="sendToIsco()">Unlock My Report</button>
    </div>
</div>

<script>
    function toPayment() {
        const name = document.getElementById('name').value;
        const mean = document.getElementById('mean').value;
        if(!name || !mean) { alert("Please enter Name and Mean Grade!"); return; }
        
        document.getElementById('displayUser').innerText = name;
        document.getElementById('formScreen').style.display = "none";
        document.getElementById('paymentGate').style.display = "block";
        window.scrollTo(0,0);
    }

    function sendToIsco() {
        const code = document.getElementById('mpesaCode').value;
        if(code.length < 6) { alert("Please enter a valid M-PESA code."); return; }

        // Grabbing all data to send to your WhatsApp
        const name = document.getElementById('name').value;
        const mean = document.getElementById('mean').value;
        const index = document.getElementById('index').value;
        const m = document.getElementById('mth').value;
        const e = document.getElementById('eng').value;
        const k = document.getElementById('kis').value;
        const b = document.getElementById('bio').value;
        const c = document.getElementById('chem').value;

        const msg = `PREMIUM ANALYSIS REQUEST%0AName: ${name}%0AIndex: ${index}%0AGrade: ${mean}%0A---%0AMaths: ${m}, Eng: ${e}, Kis: ${k}, Bio: ${b}, Chem: ${c}%0A---%0AM-PESA CODE: ${code}`;
        
        window.location.href = `https://wa.me/254746939408?text=${msg}`;
    }
</script>

</body>
</html>
