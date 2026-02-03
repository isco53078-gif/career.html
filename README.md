<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KCSE 2026 Career AI | IscoTech</title>
    <style>
        :root { --navy: #000814; --gold: #ffc300; --mpesa: #1e7e34; }
        body { font-family: 'Segoe UI', sans-serif; background: #f0f2f5; margin: 0; }
        .header { background: var(--navy); color: white; padding: 40px 10px; text-align: center; border-bottom: 5px solid var(--gold); }
        .container { padding: 15px; max-width: 500px; margin: auto; }
        .card { background: white; padding: 25px; border-radius: 20px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); margin-top: -30px; }
        input, select { width: 100%; padding: 14px; margin: 10px 0; border: 2px solid #ddd; border-radius: 10px; font-size: 16px; box-sizing: border-box; }
        .btn { width: 100%; padding: 18px; border: none; border-radius: 50px; font-weight: 800; cursor: pointer; font-size: 1.1em; margin-top: 10px; }
        
        /* Dynamic Results */
        #reportCard { display: none; text-align: left; background: #fffdf0; padding: 20px; border: 2px solid var(--gold); border-radius: 15px; margin-top: 20px; }
        .badge { background: var(--gold); color: black; padding: 4px 8px; border-radius: 4px; font-weight: bold; font-size: 0.9em; }
        .lock-notice { background: #fee2e2; border-radius: 10px; padding: 15px; margin-top: 15px; border: 1px solid #ef4444; }
    </style>
</head>
<body>

<div class="header">
    <h1>Placement AI 🇰🇪</h1>
    <p>Official 2025/2026 Career Pathways</p>
</div>

<div class="container">
    <div class="card" id="formBox">
        <h3>Step 1: Student Profile</h3>
        <input type="text" id="sName" placeholder="Student Full Name">
        <select id="sGrade">
            <option value="">Select Mean Grade</option>
            <option value="A">A / A-</option>
            <option value="B">B+ / B / B-</option>
            <option value="Cplus">C+ (University Entry)</option>
            <option value="C">C / C- (Diploma Track)</option>
            <option value="D">D+ / D (Certificate Track)</option>
            <option value="E">E (Artisan Track)</option>
        </select>
        <input type="text" id="sSubject" placeholder="Best Subject (e.g. Math, Biology)">
        
        <button class="btn" style="background:var(--navy); color:white;" onclick="generateReport()">Check My Eligibility</button>
    </div>

    <div id="reportCard">
        <h2 id="outName" style="margin-top:0;"></h2>
        <p><b>Placement Status:</b> <span class="badge" id="outLevel"></span></p>
        <p><b>Recommended Courses:</b></p>
        <ul id="outCourses" style="font-size: 0.95em;"></ul>
        <p><b>Top Institutions:</b></p>
        <p id="outSchools" style="background:#f1f1f1; padding:10px; border-radius:8px; font-size: 0.9em;"></p>

        <div class="lock-notice">
            <p style="margin:0; font-weight:bold; color:#b91c1c;">⚠️ PREMIUM DATA LOCKED</p>
            <p style="font-size:0.85em; margin:5px 0;">To see **Cluster Points** and **Full Admission List**, pay <b>100/-</b> to <b>0746939408</b>.</p>
            <button class="btn" style="background:var(--mpesa); color:white;" onclick="payAndVerify()">Verify 100/- & Unlock</button>
        </div>
    </div>
</div>

<script>
    function generateReport() {
        const name = document.getElementById('sName').value;
        const grade = document.getElementById('sGrade').value;
        const subject = document.getElementById('sSubject').value;

        if(!name || !grade) { alert("Please fill in your details!"); return; }

        // TRIGGER MONETAG AD (You earn Dollars)
        window.open("https://otieu.com/4/10560010", "_blank");

        // PROCESS RESULTS
        document.getElementById('reportCard').style.display = "block";
        document.getElementById('outName').innerText = "Results for " + name;

        let level, courses, schools;

        if(grade === "A" || grade === "B") {
            level = "Degree (Direct University Placement)";
            courses = ["Medicine & Surgery", "Computer Science", "Engineering", "Law"];
            schools = "UoN, JKUAT, Kenyatta University, Egerton.";
        } else if(grade === "Cplus") {
            level = "University Degree / Higher Diploma";
            courses = ["Education (Arts/Science)", "Nursing (BSc)", "Agribusiness", "IT"];
            schools = "Maseno, Tom Mboya University, MKU, KMTC Nairobi.";
        } else if(grade === "C") {
            level = "Diploma (Level 6)";
            courses = ["Diploma in ICT", "Diploma in Nursing", "Building & Construction", "Pharmacy"];
            schools = "Homa Bay National Poly, Mawego TTI, KMTC Homa Bay.";
        } else if(grade === "D") {
            level = "Certificate (Level 5)";
            courses = ["Electrical Installation", "Plumbing", "Fashion Design", "Catering"];
            schools = "Sikri Technical, Mawego TTI, Vocational Centers.";
        } else {
            level = "Artisan (Level 4)";
            courses = ["Masonry", "Welding", "Hairdressing"];
            schools = "Local Youth Polytechnics and Vocational Centers.";
        }

        document.getElementById('outLevel').innerText = level;
        document.getElementById('outSchools').innerText = schools;
        
        const list = document.getElementById('outCourses');
        list.innerHTML = "";
        courses.forEach(c => { list.innerHTML += `<li>${c}</li>`; });
    }

    function payAndVerify() {
        const name = document.getElementById('sName').value;
        // Trigger Second Ad for extra profit
        window.open("https://otieu.com/4/10560010", "_blank");
        
        // Redirect to WhatsApp for the 100/- confirmation
        const msg = `Hello IscoTech, I have paid 100/- for the KCSE Career Report for ${name}. Please send the full PDF.`;
        window.location.href = `https://wa.me/254746939408?text=${encodeURIComponent(msg)}`;
    }
</script>

</body>
</html>
