<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Career Analysis | IscoTech Academy</title>
    <style>
        :root { --navy: #000814; --gold: #ffc300; --mpesa: #28a745; }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #f8f9fa; margin: 0; color: #333; }
        
        .top-header { background: var(--navy); color: white; padding: 40px 20px; text-align: center; border-bottom: 6px solid var(--gold); }
        .container { max-width: 450px; margin: -30px auto 50px; padding: 0 15px; }
        .card { background: #ffffff; padding: 30px; border-radius: 20px; box-shadow: 0 10px 30px rgba(0,0,0,0.15); border: 1px solid #eee; }
        
        input, select { width: 100%; padding: 15px; margin: 12px 0; border: 2px solid #e2e8f0; border-radius: 12px; font-size: 16px; box-sizing: border-box; }
        input:focus { border-color: var(--gold); outline: none; }
        
        .btn { width: 100%; padding: 18px; border: none; border-radius: 50px; font-weight: 800; cursor: pointer; font-size: 1.1em; transition: 0.3s; }
        .submit-btn { background: var(--navy); color: white; }
        
        /* Paywall Screens */
        #paymentArea { display: none; text-align: center; }
        .locked-badge { background: #fee2e2; color: #b91c1c; padding: 8px 15px; border-radius: 10px; font-size: 0.9em; font-weight: bold; display: inline-block; margin-bottom: 15px; }
        .mpesa-box { background: #f0fff4; border: 2px dashed var(--mpesa); padding: 25px; border-radius: 15px; margin: 20px 0; }
        
        .footer { text-align: center; padding: 30px; font-size: 0.9em; color: #666; background: #fff; border-top: 1px solid #eee; margin-top: 50px; }
        .contact-link { color: var(--navy); text-decoration: none; font-weight: bold; display: block; margin: 10px 0; }
    </style>
</head>
<body>

<div class="top-header">
    <h1 style="margin:0;">ISCOTECH ACADEMY</h1>
    <p>Premium Career Placement Hub</p>
</div>

<div class="container">
    <div class="card">
        <div id="dataInput">
            <h3 style="margin-top:0;">Career Eligibility Form</h3>
            <p style="font-size:0.85em; color:#666;">Enter your KCSE 2025 details to generate your official placement report.</p>
            
            <input type="text" id="stuName" placeholder="Enter Full Name" required>
            <select id="stuGrade" required>
                <option value="">Select Mean Grade</option>
                <option>A</option><option>A-</option><option>B+</option><option>B</option>
                <option>B-</option><option>C+</option><option>C</option><option>C-</option>
                <option>D+</option><option>D</option><option>E</option>
            </select>
            <input type="text" id="stuSub" placeholder="Your Best Subject (e.g. Mathematics)">
            
            <button class="btn submit-btn" onclick="lockAndPay()">Process My Eligibility</button>
        </div>

        <div id="paymentArea">
            <div class="locked-badge">🔒 PLACEMENT REPORT LOCKED</div>
            <p>Report for <b><span id="userName"></span></b> is ready, but requires activation.</p>
            
            <div class="mpesa-box">
                <p style="margin: 0; font-size: 0.9em;">To unlock, send <b>KES 100</b> to:</p>
                <p style="margin: 10px 0;"><b style="font-size: 1.6em; color: var(--mpesa);">0746939408</b><br>
                <span style="font-size: 0.8em; color: #555;">Name: ISCOTECH ACADEMY</span></p>
            </div>

            <p style="font-size: 0.8em; color: #666;">Once you receive the M-PESA confirmation, click below to verify and receive your course list.</p>
            <button class="btn" style="background:var(--mpesa); color:white;" onclick="verifyOnWhatsApp()">Verify Payment & Unlock</button>
        </div>
    </div>
</div>

<div class="footer">
    <h4>IscoTech Support Office</h4>
    <a href="https://wa.me/254746939408" class="contact-link">WhatsApp: 0746939408</a>
    <a href="mailto:isco53078@gmail.com" class="contact-link">Email: isco53078@gmail.com</a>
    <p>📍 Opposite Equity Bank, Homa Bay Town</p>
    <p style="opacity: 0.6; font-size: 0.8em;">© 2026 IscoTech Academy Hub. All Rights Reserved.</p>
</div>

<script>
    // CLEAN SCRIPT: NO EXTERNAL LINKS OR SCRIPTS
    function lockAndPay() {
        const name = document.getElementById('stuName').value;
        const grade = document.getElementById('stuGrade').value;

        if(!name || !grade) {
            alert("Please fill in your name and grade to proceed.");
            return;
        }

        // Hide form, show payment
        document.getElementById('userName').innerText = name;
        document.getElementById('dataInput').style.display = "none";
        document.getElementById('paymentArea').style.display = "block";
        window.scrollTo(0,0);
    }

    function verifyOnWhatsApp() {
        const name = document.getElementById('stuName').value;
        const grade = document.getElementById('stuGrade').value;
        const sub = document.getElementById('stuSub').value;
        
        // Direct WhatsApp link with no middle-man
        const text = `PREMIUM UNLOCK REQUEST%0A----------------------%0AName: ${name}%0AGrade: ${grade}%0ASubject: ${sub}%0A----------------------%0AI have paid 100/- to 0746939408. Please send my 2026 course and school list.`;
        
        window.location.href = `https://wa.me/254746939408?text=${text}`;
    }
</script>

</body>
</html>
