<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Career Master | IscoTech Academy</title>
    <style>
        :root { --navy: #000814; --gold: #ffc300; --mpesa: #28a745; }
        body { font-family: 'Segoe UI', sans-serif; background: #f0f2f5; margin: 0; padding-bottom: 50px; }
        .header { background: var(--navy); color: white; padding: 40px 15px; text-align: center; border-bottom: 5px solid var(--gold); }
        .container { max-width: 650px; margin: -30px auto 50px; padding: 0 15px; }
        .card { background: white; padding: 30px; border-radius: 20px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); }
        
        .subject-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; margin-top: 10px; }
        h4 { margin: 20px 0 5px 0; color: var(--navy); border-bottom: 2px solid var(--gold); display: inline-block; }
        input, select { width: 100%; padding: 12px; margin: 5px 0; border: 1px solid #ddd; border-radius: 8px; box-sizing: border-box; font-size: 14px; }
        .btn { width: 100%; padding: 18px; border: none; border-radius: 50px; font-weight: 800; cursor: pointer; font-size: 1.1em; margin-top: 20px; }
        
        #paymentScreen, #resultScreen { display: none; }
        .result-box { text-align: left; background: #fffdf0; padding: 25px; border: 2px solid var(--gold); border-radius: 15px; }
        .mpesa-card { background: #f0fff4; border: 2px dashed var(--mpesa); padding: 20px; border-radius: 15px; margin: 20px 0; text-align: center; }
    </style>
</head>
<body>

<div class="header">
    <h1>IscoTech Career AI</h1>
    <p>Instant Automated Subject Analysis</p>
</div>

<div class="container">
    <div class="card" id="inputScreen">
        <h3>1. Student Profile</h3>
        <input type="text" id="stuName" placeholder="Full Student Name">
        <select id="mean"><option value="">MEAN GRADE</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>

        <h4>2. Core Subjects</h4>
        <div class="subject-grid">
            <select id="mat"><option value="">Maths</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
            <select id="eng"><option value="">English</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
            <select id="kis"><option value="">Kiswahili</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
        </div>

        <h4>3. Sciences & Electives</h4>
        <div class="subject-grid">
            <select id="bio"><option value="">Biology</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
            <select id="phy"><option value="">Physics</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
            <select id="com"><option value="">Computer Studies</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
            <select id="bus"><option value="">Business Studies</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
            <select id="agr"><option value="">Agriculture</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
            <select id="his"><option value="">History/Geo</option><option>A</option><option>B</option><option>C</option><option>D</option><option>E</option></select>
        </div>
        <button class="btn" style="background:var(--navy); color:white;" onclick="toPayment()">Analyze Full Eligibility</button>
    </div>

    <div class="card" id="paymentScreen">
        <h3 style="color:red;">🔒 PAYMENT REQUIRED</h3>
        <p>Your full career mapping is ready for <b><span id="uName"></span></b>.</p>
        <div class="mpesa-card">
            <p>Send <b>100/-</b> to M-PESA:<br>
            <b style="font-size:1.5em; color:var(--mpesa);">0746939408</b><br>
            (ISCOTECH ACADEMY)</p>
        </div>
        <input type="text" id="mCode" placeholder="Enter M-PESA Code (e.g. TKB8...)">
        <button class="btn" style="background:var(--mpesa); color:white;" onclick="showResults()">Unlock & View Results Now</button>
    </div>

    <div class="card" id="resultScreen">
        <div class="result-box">
            <h2 id="resTitle" style="margin-top:0; color:var(--navy);"></h2>
            <p><b>Level:</b> <span id="resLevel" style="color:var(--mpesa); font-weight:bold;"></span></p>
            <hr>
            <p><b>Recommended Paths:</b></p>
            <ul id="resCourses"></ul>
            <p><b>Top Institutions:</b></p>
            <p id="resSchools" style="background:#eee; padding:10px; border-radius:8px; font-size:0.9em;"></p>
            <p><b>Workplaces:</b></p>
            <p id="resWork" style="font-size:0.9em; color:#444;"></p>
        </div>
        <button class="btn" style="background:var(--navy); color:white;" onclick="window.print()">Download Report</button>
    </div>
</div>

<script>
    function toPayment() {
        const name = document.getElementById('stuName').value;
        if(!name) { alert("Please enter your name!"); return; }
        document.getElementById('uName').innerText = name;
        document.getElementById('inputScreen').style.display = "none";
        document.getElementById('paymentScreen').style.display = "block";
    }

    function showResults() {
        const code = document.getElementById('mCode').value;
        if(code.length < 5) { alert("Enter a valid M-PESA code!"); return; }

        const name = document.getElementById('stuName').value;
        const mean = document.getElementById('mean').value;
        const comp = document.getElementById('com').value;

        let level, courses, schools, work;

        // AUTOMATED CAREER LOGIC
        if(mean === "A" || mean === "B") {
            level = "Degree Placement";
            schools = "UoN, JKUAT, Kenyatta University, Maseno.";
            work = "Government, Tech Companies, Hospitals, Law Firms.";
            courses = (comp === "A" || comp === "B") ? ["Computer Science", "Software Engineering"] : ["Business", "Medicine", "Law"];
        } else if(mean === "C") {
            level = "Diploma Placement";
            schools = "Homa Bay National Poly, Mawego TTI, KMTC.";
            work = "Private Offices, Construction, County Hospitals.";
            courses = ["ICT Diploma", "Nursing", "Electrical Eng", "Accounting"];
        } else {
            level = "Certificate / Artisan";
            schools = "Mawego TTI, Sikri Technical, Youth Polytechnics.";
            work = "Self-employment, Garages, Hotels, Workshops.";
            courses = ["Plumbing", "Masonry", "Catering", "Mechanics"];
        }

        document.getElementById('resTitle').innerText = "Report for " + name;
        document.getElementById('resLevel').innerText = level;
        document.getElementById('resSchools').innerText = schools;
        document.getElementById('resWork').innerText = work;
        const list = document.getElementById('resCourses');
        list.innerHTML = "";
        courses.forEach(c => { list.innerHTML += `<li>${c}</li>`; });

        document.getElementById('paymentScreen').style.display = "none";
        document.getElementById('resultScreen').style.display = "block";
    }
</script>

</body>
</html>
