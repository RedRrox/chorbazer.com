<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CHOR BAZER | FF UID TOP UP</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;800&family=Rajdhani:wght@500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --neon-yellow: #ccff00;
            --dark-bg: #0a0a0a;
            --card-bg: #151515;
            --text-color: #ffffff;
            --bkash-color: #d12053;
            --border-color: #222;
        }

        .light-mode {
            --dark-bg: #f0f2f5;
            --card-bg: #ffffff;
            --text-color: #1a1a1a;
            --border-color: #ddd;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Rajdhani', sans-serif; transition: 0.3s; }
        body { background: var(--dark-bg); color: var(--text-color); padding-bottom: 80px; }

        header { background: #000; padding: 20px; text-align: center; border-bottom: 2px solid var(--neon-yellow); position: relative; }
        .logo { font-family: 'Orbitron', sans-serif; font-size: 28px; color: var(--neon-yellow); letter-spacing: 3px; }

        .theme-toggle { position: absolute; right: 15px; top: 20px; background: var(--neon-yellow); border: none; padding: 5px 12px; border-radius: 20px; cursor: pointer; font-weight: bold; font-size: 12px; }

        .container { max-width: 600px; margin: 20px auto; padding: 15px; }
        .box { background: var(--card-bg); border: 1px solid var(--border-color); padding: 20px; border-radius: 12px; margin-bottom: 20px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
        h2 { font-size: 18px; margin-bottom: 15px; color: var(--neon-yellow); text-transform: uppercase; border-left: 4px solid var(--neon-yellow); padding-left: 10px; }

        input[type="text"] { width: 100%; padding: 15px; background: rgba(0,0,0,0.05); border: 1px solid var(--border-color); color: var(--text-color); border-radius: 8px; font-size: 18px; text-align: center; font-weight: bold; outline: none; }

        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .item { background: rgba(0,0,0,0.03); border: 1px solid var(--border-color); padding: 20px; border-radius: 10px; cursor: pointer; text-align: center; }
        .item.active { border-color: var(--neon-yellow); background: rgba(204, 255, 0, 0.1); }
        .item .price { color: var(--neon-yellow); font-weight: bold; font-size: 22px; display: block; }

        /* Fake Order Notification Styling */
        #notification-box {
            background: rgba(204, 255, 0, 0.05);
            border: 1px dashed var(--neon-yellow);
            padding: 12px;
            border-radius: 8px;
            margin-top: 15px;
            font-size: 15px;
            text-align: center;
            font-weight: bold;
            color: var(--neon-yellow);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { opacity: 0.7; }
            50% { opacity: 1; }
            100% { opacity: 0.7; }
        }

        .copy-btn { background: #eee; border: 1px solid #ccc; padding: 4px 10px; border-radius: 4px; font-size: 11px; cursor: pointer; margin-left: 10px; color: #333; }
        
        /* Payment UI */
        .logo-crop { width: 80px; height: 45px; overflow: hidden; display: flex; justify-content: center; }
        .logo-crop img { width: 80px; height: auto; }

        #bkash-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 9999; justify-content: center; align-items: center; }
        .bkash-content { background: #fff; width: 92%; max-width: 400px; border-radius: 12px; overflow: hidden; color: #000; }
        .bkash-body { background: var(--bkash-color); color: #fff; padding: 20px; }
        
        .verify-btn { width: 90%; margin: 15px auto; display: block; padding: 15px; background: #d00000; color: #fff; border: none; font-weight: bold; border-radius: 8px; cursor: pointer; }
        .btn-buy { width: 100%; padding: 18px; background: var(--neon-yellow); color: #000; border: none; border-radius: 8px; font-weight: bold; font-size: 20px; cursor: pointer; }
    </style>
</head>
<body>

<header>
    <div class="logo">CHOR BAZER</div>
    <button class="theme-toggle" onclick="toggleTheme()">☀️ LIGHT</button>
</header>

<div class="container">
    <div id="notification-box">
        🚀 <span id="notify-text">Checking for recent orders...</span>
    </div>

    <div class="box" style="margin-top: 20px;">
        <h2>1. Player UID</h2>
        <input type="text" id="uid-input" placeholder="Enter Player UID" oninput="updateID()">
    </div>

    <div class="box">
        <h2>2. Select Pack</h2>
        <div class="grid">
            <div class="item" onclick="selectPack(this, 'Weekly Member', 140)">
                <span>Weekly Member</span>
                <span class="price">৳ 140</span>
            </div>
            <div class="item" onclick="selectPack(this, 'Monthly Member', 650)">
                <span>Monthly Member</span>
                <span class="price">৳ 650</span>
            </div>
        </div>
    </div>

    <div class="box summary">
        <h2>3. Order Summary</h2>
        <p style="display:flex; justify-content:space-between;">Selected: <span id="sum-pack">-</span></p>
        <p style="display:flex; justify-content:space-between;">Player ID: <span id="sum-id">-</span></p>
        <div style="color:var(--neon-yellow); font-size:24px; font-weight:bold; margin-top:10px;">Total: ৳ <span id="sum-total">0</span></div>

        <h2 style="margin-top: 20px;">4. Payment Method</h2>
        <div class="method active" style="border: 1px solid var(--bkash-color); padding: 15px; border-radius: 10px; display: flex; align-items: center; justify-content: center; background: rgba(209, 32, 83, 0.05);">
            <div class="logo-crop"><img src="bikashlogo.png" alt="bkash"></div>
        </div>
        <button class="btn-buy" style="margin-top:15px;" onclick="openPayment()">BUY NOW</button>
    </div>
</div>

<div id="bkash-modal">
    <div class="bkash-content">
        <div style="text-align:center; padding:10px;"><img src="bikashlogo.png" width="100"></div>
        <div class="bkash-body">
            <p style="text-align: center; font-weight: bold; margin-bottom: 15px;">ট্রানজেকশন আইডি দিন</p>
            <input type="text" id="trx-input" style="width:100%; padding:12px; margin-bottom:15px; border-radius:5px; border:none; text-align:center; font-weight:bold;" placeholder="TrxID এখানে দিন">
            <div style="font-size: 13px; border-bottom: 1px solid rgba(255,255,255,0.2); padding-bottom: 8px; margin-bottom: 8px;">● "Send Money" অপশন ব্যবহার করুন।</div>
            <div style="font-size: 13px; border-bottom: 1px solid rgba(255,255,255,0.2); padding-bottom: 8px; margin-bottom: 8px;">● নম্বরঃ <b id="bkash-num">017797722010</b> <button class="copy-btn" onclick="copyNumber()">COPY</button></div>
            <div style="font-size: 13px; margin-bottom: 8px;">● টাকার পরিমাণঃ ৳ <b id="pay-amount">0</b></div>
        </div>
        <div style="background:#fff9c4; color:#d32f2f; padding:10px; font-size:12px; text-align:center; font-weight:bold;">
            ⚠️ পেমেন্টের ৩০-৪০ মিনিটের মধ্যে ডায়মন্ড পৌঁছে যাবে।
        </div>
        <button class="verify-btn" onclick="verifyOrder()">VERIFY</button>
    </div>
</div>

<script>
    let selectedPrice = 0;
    let selectedPackName = "";

    // --- FAKE ORDER LOGIC ---
    const fakeNames = ["ID 2548****", "ID 9961****", "ID 1002****", "UID 3365****", "ID 7741****", "UID 8520****", "ID 4410****"];
    const fakePacks = ["Weekly Member", "Monthly Member"];
    
    function showFakeOrder() {
        const text = document.getElementById('notify-text');
        const randomName = fakeNames[Math.floor(Math.random() * fakeNames.length)];
        const randomPack = fakePacks[Math.floor(Math.random() * fakePacks.length)];
        
        text.innerText = `🔥 User ${randomName} just purchased ${randomPack}!`;
        
        // ৫ সেকেন্ড পর পর পাল্টাবে
        setTimeout(showFakeOrder, 5000);
    }
    // গেম অন! প্রথমবার রান করলাম
    showFakeOrder();

    function toggleTheme() {
        document.body.classList.toggle('light-mode');
        const btn = document.querySelector('.theme-toggle');
        btn.innerText = document.body.classList.contains('light-mode') ? "🌙 DARK" : "☀️ LIGHT";
    }

    function copyNumber() {
        const num = document.getElementById('bkash-num').innerText;
        navigator.clipboard.writeText(num);
        alert("Number Copied!");
    }

    function updateID() {
        document.getElementById('sum-id').innerText = document.getElementById('uid-input').value || "-";
    }

    function selectPack(el, name, price) {
        document.querySelectorAll('.item').forEach(i => i.classList.remove('active'));
        el.classList.add('active');
        selectedPrice = price;
        selectedPackName = name;
        document.getElementById('sum-pack').innerText = name;
        document.getElementById('sum-total').innerText = price;
        document.getElementById('pay-amount').innerText = price;
    }

    function openPayment() {
        if(!document.getElementById('uid-input').value || selectedPrice === 0) {
            alert("UID এবং প্যাক সিলেক্ট করুন!");
            return;
        }
        document.getElementById('bkash-modal').style.display = 'flex';
    }

    function verifyOrder() {
        if(document.getElementById('trx-input').value.length < 5) {
            alert("ভুল ট্রানজেকশন আইডি!");
        } else {
            alert("অর্ডার সফল! ৩০-৪০ মিনিটের মধ্যে ডেলিভারি পাবেন।");
            location.reload();
        }
    }
</script>

</body>
</html>
