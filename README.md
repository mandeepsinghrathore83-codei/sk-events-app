<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SK EVENTS - Dashboard</title>
    <style>
        :root { --gold: #d4af37; --dark: #0b0b0b; }
        body { background: var(--dark); color: white; font-family: sans-serif; text-align: center; margin: 0; }
        .header { background: #222; padding: 20px; border-bottom: 2px solid var(--gold); }
        .container { padding: 15px; max-width: 400px; margin: auto; }
        .card { background: #1a1a1a; border: 1px solid var(--gold); border-radius: 15px; padding: 20px; margin-top: 20px; }
        input { width: 90%; padding: 12px; margin: 10px 0; border-radius: 8px; border: 1px solid #444; background: #222; color: white; }
        .btn { background: var(--gold); color: black; border: none; padding: 12px; width: 100%; font-weight: bold; border-radius: 8px; cursor: pointer; margin-top: 10px; }
        .service-card { background: #222; border-radius: 10px; padding: 15px; margin-top: 15px; border-left: 4px solid var(--gold); text-align: left; }
        .hidden { display: none !important; }
    </style>
</head>
<body>

    <div class="header">
        <h1 style="color: var(--gold); margin: 0;">SK EVENTS</h1>
    </div>

    <div class="container">
        <div id="loginScreen" class="card">
            <h3>स्वागत है! लॉगिन करें</h3>
            <input type="text" id="userName" placeholder="आपका नाम">
            <input type="email" id="userEmail" placeholder="आपका Gmail">
            <button class="btn" onclick="sendOTP()">ओटीपी पाएँ</button>
        </div>

        <div id="otpSection" class="card hidden">
            <p style="color: var(--gold);">Gmail पर कोड भेजा गया है</p>
            <input type="number" id="otpValue" placeholder="कोड डालें">
            <button class="btn" onclick="verifyOTP()">प्रवेश करें</button>
        </div>

        <div id="dashboard" class="hidden">
            <div class="card">
                <h2 id="welcomeMsg" style="color: #2ecc71;"></h2>
                <p>आप सफलतापूर्वक लॉगिन कर चुके हैं! ✅</p>
            </div>

            <h3 style="text-align: left; color: var(--gold);">हमारी सेवाएं:</h3>
            
            <div class="service-card">
                <h4>🎧 DJ ऑपरेटिंग</h4>
                <button class="btn" onclick="alert('बुकिंग रिक्वेस्ट भेज दी गई!')">बुक करें</button>
            </div>

            <div class="service-card">
                <h4>🚗 Luxury गाड़ियाँ</h4>
                <button class="btn" onclick="alert('बुकिंग रिक्वेस्ट भेज दी गई!')">बुक करें</button>
            </div>
        </div>
    </div>

    <script>
        // ओटीपी भेजने का फंक्शन
        function sendOTP() {
            const name = document.getElementById('userName').value;
            if(!name) { alert("नाम डालें!"); return; }
            window.tempName = name;
            window.generatedOTP = "9612"; // टेस्टिंग के लिए फिक्स कोड
            alert("ओटीपी भेज दिया गया है! (टेस्टिंग कोड: 9612)");
            document.getElementById('loginScreen').classList.add('hidden');
            document.getElementById('otpSection').classList.remove('hidden');
        }

        // ओटीपी वेरिफिकेशन (सुधार के साथ)
        function verifyOTP() {
            const entered = document.getElementById('otpValue').value;
            if(entered === window.generatedOTP) {
                document.getElementById('otpSection').classList.add('hidden');
                // यहाँ सुधार किया गया है ताकि डैशबोर्ड दिखे
                document.getElementById('dashboard').style.display = 'block';
                document.getElementById('dashboard').classList.remove('hidden');
                document.getElementById('welcomeMsg').innerText = "नमस्ते, " + window.tempName + "!";
            } else {
                alert("गलत ओटीपी!");
            }
        }
    </script>
</body>
</html>
