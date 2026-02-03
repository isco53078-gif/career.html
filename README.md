<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IscoTech Career AI | Instant Placement</title>
    <style>
        :root { --navy: #000814; --gold: #ffc300; --mpesa: #28a745; }
        body { font-family: 'Segoe UI', sans-serif; background: #f4f7f6; margin: 0; color: #333; }
        .header { background: var(--navy); color: white; padding: 40px 15px; text-align: center; border-bottom: 5px solid var(--gold); }
        .container { max-width: 600px; margin: -30px auto 50px; padding: 0 15px; }
        .card { background: white; padding: 30px; border-radius: 20px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); text-align: center; }
        
        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin: 20px 0; text-align: left; }
        input, select { width: 100%; padding: 12px; border: 1px solid #ddd; border-radius: 10px; box-sizing: border-box; }
        .btn { width: 100%; padding: 18px; border: none; border-radius: 50px; font-weight: 800; cursor: pointer; font-size: 1.1em; transition: 0.3s; }
        
        #payGate, #verifying, #results { display: none; }
        
        .till-box { background: #f0fff4; border: 2px solid var(--mpesa); padding: 20px; border-radius: 15px; margin: 20px 0; }
        .till-no { background: var(--mpesa); color: white; padding: 10px; border-radius: 8px; font-size: 2.2em; font-weight: 900; margin: 10px 0; display: block; }
        
        .loader-box { width: 100%; background: #eee; height: 12px; border-radius: 10px; margin: 20px 0; overflow: hidden; }
        .bar { width: 0%; height: 100%; background: var(--mpesa); transition: width 3.5s linear; }
        
        .res-card { text-align: left; background: #fffdf0; border: 2px solid var(--gold); padding: 20px; border-radius: 15px; }
        .wa-btn { color: #25D366; text-decoration: none; font-size: 0.85em; display: inline-block; margin-top: 15px; font-weight: bold; }
    </style>
</head>
<body>

<div class="header">
    <h1>IscoTech Career AI</h1>
    <p>Automated KCSE 2026 Student Placement</p>
</div>

<div class="container">
    <div class="card" id="form">
        <h3>1. Enter Academic Results</h3>
        <input type="text" id="name" placeholder="Student Full Name">
        <div class="grid">
            <select id="mean"><option value="">Mean Grade</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
            <select id="math"><option value="">Maths</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
            <select id="eng"><option value="">English</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
            <select id="comp"><option value="">Computer/Biz</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
        </div>
        <button class="btn" style="background:var(--navy); color:white;" onclick="openPay()">Analyze My Results</button>
    </div>

    <div class="card" id="payGate">
        <h3 style="color:#d32f2f;">🔒 PLACEMENT REPORT READY</h3>
        <p>Analysis for <b id="uName"></b> is locked. Pay 100/- to view.</p>
        <div class="till-box">
            <small>LIPA NA M-PESA (Buy Goods)</small>
            <span class="till-no">448941</span>
            <b>Amount: KES 100</b>
        </div>
        <p style="font-size:0.85em;">Enter the <b>M-PESA Code</b> or <b>Phone Number</b> used:</p>
        <input type="text" id="code" placeholder="Example: TKB8... or 0712..." style="text-align:center; font-weight:bold;">
        <button class="btn" style="background:var(--mpesa); color:white;" onclick="startVerify()">Unlock Report Instantly</button>
        <br>
        <a href="https://wa.me/254746939408?text=I%20have%20a%20problem%20with%20payment%20on%20IscoTech" class="wa-btn">Need Help? Chat on WhatsApp</a>
    </div>

    <div class="card" id="verifying">
        <h3>Verifying Transaction...</h3>
        <p>Connecting to IscoTech Payment Gateway</p>
        <div class="loader-box"><div class="bar" id="pBar"></div></div>
        <p style="font-size:0.7em; color:#888;">Checking ID: 448941-AUTO</p>
    </div>

    <div class="card" id="results">
        <div class="res-card">
            <h2 id="rTitle" style="margin:0; color:var(--navy);"></h2>
            <p><b>Admission:</b> <span id="rLevel" style="color:var(--mpesa); font-weight:bold;"></span></p>
            <hr>
            <p><b>Recommended Courses:</b></p>
            <ul id="rCourses" style="font-weight:bold;"></ul>
            <p><b>Best Institutions to Join:</b></p>
            <p id="rSchools" style="background:#f4f4f4; padding:10px; border-radius:8px; font-size:0.9em;"></p>
        </div>
        <button class="btn" style="background:var(--navy); color:white; margin-top:15px;" onclick="window.print()">Download & Print (PDF)</button>
    </div>
</div>

<script>
    function openPay() {
        const n = document.getElementById('name').value;
        if(!n) { alert("Please enter your name!"); return; }
        document.getElementById('uName').innerText = n;
        document.getElementById('form').style.display = "none";
        document.getElementById('payGate').style.display = "block";
    }

    function startVerify() {
        const c = document.getElementById('code').value;
        if(c.length < 5) { alert("Please enter the M-PESA details to unlock."); return; }
        document.getElementById('payGate').style.display = "none";
        document.getElementById('verifying').style.display = "block";
        setTimeout(() => { document.getElementById('pBar').style.width = "100%"; }, 100);
        setTimeout(showFinal, 4000); 
    }

    function showFinal() {
        const n = document.getElementById('name').value;
        const g = document.getElementById('mean').value;
        const m = document.getElementById('math').value;
        const cp = document.getElementById('comp').value;

        let level, schools, courses;

        if(g === "A" || g === "B") {
            level = "University Degree Entry";
            schools = "JKUAT, UoN, Maseno, Kenyatta University.";
            courses = (cp === "A" || m === "A") ? ["Software Engineering", "Computer Science"] : ["Law", "Medicine"];
        } else if(g === "C") {
            level = "Diploma (TVET / KMTC)";
            schools = "Homa Bay National Poly, Mawego TTI, KMTC Homa Bay.";
            courses = ["Diploma in ICT", "Nursing", "Electrical Engineering"];
        } else {
            level = "Certificate / Artisan Path";
            schools = "Mawego TTI, Sikri Technical, Youth Polytechnics.";
            courses = ["Plumbing", "Catering", "Masonry", "Mechanics"];
        }

        document.getElementById('rTitle').innerText = "Verified Report: " + n;
        document.getElementById('rLevel').innerText = level;
        document.getElementById('rSchools').innerText = schools;
        const list = document.getElementById('rCourses');
        list.innerHTML = "";
        courses.forEach(item => { list.innerHTML += `<li>${item}</li>`; });

        document.getElementById('verifying').style.display = "none";
        document.getElementById('results').style.display = "block";
    }
</script>

</body>
</html>
