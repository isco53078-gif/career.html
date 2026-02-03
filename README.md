<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Career Placement | IscoTech Academy</title>
    <style>
        :root { --navy: #001d3d; --gold: #ffc300; --mpesa: #28a745; --white: #ffffff; }
        body { font-family: 'Poppins', sans-serif; background: #f4f7f6; margin: 0; color: #333; }
        
        /* Header & Branding */
        .header { background: var(--navy); color: white; padding: 50px 20px; text-align: center; border-bottom: 6px solid var(--gold); }
        .consultant-badge { background: var(--gold); color: var(--navy); padding: 5px 15px; border-radius: 20px; font-weight: bold; font-size: 0.8em; display: inline-block; margin-bottom: 10px; }
        
        .container { max-width: 450px; margin: -40px auto 40px; padding: 0 15px; }
        .card { background: white; padding: 30px; border-radius: 25px; box-shadow: 0 15px 40px rgba(0,0,0,0.12); border: 1px solid #eee; }
        
        input, select { width: 100%; padding: 15px; margin: 12px 0; border: 2px solid #e2e8f0; border-radius: 12px; font-size: 16px; box-sizing: border-box; outline: none; transition: 0.3s; }
        input:focus { border-color: var(--gold); }
        
        .btn { width: 100%; padding: 18px; border: none; border-radius: 50px; font-weight: 800; cursor: pointer; font-size: 1.1em; transition: 0.3s; }
        .submit-btn { background: var(--navy); color: white; box-shadow: 0 4px 12px rgba(0,29,61,0.3); }
        
        /* Payment Section */
        #paymentGate { display: none; text-align: center; }
        .mpesa-instructions { background: #f0fff4; border: 2px dashed var(--mpesa); padding: 20px; border-radius: 15px; margin: 20px 0; }
        
        /* Professional Footer */
        .footer-contacts { background: #fff; border-top: 1px solid #eee; padding: 25px 15px; margin-top: 40px; text-align: center; font-size: 0.9em; }
        .contact-item { margin: 10px 0; color: var(--navy); text-decoration: none; display: block; font-weight: 600; }
        .contact-item i { color: var(--gold); margin-right: 8px; }
    </style>
</head>
<body>

<div class="header">
    <div class="consultant-badge">OFFICIAL 2026 CAREER CONSULTANT</div>
    <h1 style="margin:0; letter-spacing: 1px;">ISCOTECH PREMIUM</h1>
    <p>KCSE 2025 Career & Placement Analysis</p>
</div>

<div class="container">
    <div class="card">
        <div id="inputForm">
            <h3 style="margin-top:0;">1. Analysis Request</h3>
            <p style="font-size:0.85em; color:#666;">Enter your details precisely as they appear on your result slip.</p>
            
            <input type="text" id="name" placeholder="Full Name (as per KCSE)" required>
            <select id="grade" required>
                <option value="">Select Mean Grade</option>
                <option>A / A-</option><option>B+</option><option>B</option>
                <option>B-</option><option>C+</option><option>C</option>
                <option>C-</option><option>D+</option><option>D</option><option>E</option>
            </select>
            <input type="text" id="subjects" placeholder="Strongest Subjects (e.g. Math, Eng, Bio)">
            
            <button class="btn submit-btn" onclick="lockAndShowPayment()">Generate My Career Report</button>
        </div>

        <div id="paymentGate">
            <h3 style="color: var(--mpesa);">✓ Data Registered</h3>
            <p>To generate the full placement report for <b><span id="userName"></span></b>, pay the processing fee.</p>
            
            <div class="mpesa-instructions">
                <p style="color:red; font-weight:bold; font-size:0.8em; margin-bottom:5px;">AWAITING KES 100.00</p>
                <p style="margin: 0;">Send <b>100/-</b> to M-PESA:<br>
                <b style="font-size: 1.6em; color: #28a745;">0746939408</b><br>
                Name: <b>ISCOTECH ACADEMY</b></p>
            </div>

            <button class="btn" style="background:var(--mpesa); color:white;" onclick="sendConfirmation()">Verify & Unlock via WhatsApp</button>
            <p style="font-size:0.75em; color:#888; margin-top:15px;">Your report includes: Degree/Diploma eligibility, 5 Recommended Universities, and KUCCPS Cluster Guidelines.</p>
        </div>
    </div>
</div>

<div class="footer-contacts">
    <h4 style="margin-bottom:15px; color:var(--navy);">Need Help? Contact Our Office</h4>
    <a href="tel:+254746939408" class="contact-item">📞 Phone: 0746939408</a>
    <a href="https://wa.me/254746939408" class="contact-item">💬 WhatsApp: 0746939408</a>
    <a href="mailto:isco53078@gmail.com" class="contact-item">📧 Email: isco53078@gmail.com</a>
    <p style="font-size: 0.8em; color: #999; margin-top: 20px;">📍 Location: Opposite Equity Bank, Homa Bay Town<br>© 2026 IscoTech Academy Hub</p>
</div>

<script>
    function lockAndShowPayment() {
        const nameInput = document.getElementById('name').value;
        const gradeInput = document.getElementById('grade').value;

        if(!nameInput || !gradeInput) {
            alert("Please fill in your name and grade to proceed.");
            return;
        }

        document.getElementById('userName').innerText = nameInput;
        document.getElementById('inputForm').style.display = "none";
        document.getElementById('paymentGate').style.display = "block";
        window.scrollTo(0,0);
    }

    function sendConfirmation() {
        const name = document.getElementById('name').value;
        const grade = document.getElementById('grade').value;
        const subjects = document.getElementById('subjects').value;
        
        const text = `PREMIUM CAREER UNLOCK%0A----------------------%0AName: ${name}%0AGrade: ${grade}%0ASubjects: ${subjects}%0A----------------------%0AI have sent KES 100 to 0746939408. Please send my 2026 Placement Report PDF.`;
        
        window.location.href = `https://wa.me/254746939408?text=${text}`;
    }
</script>

</body>
</html>
