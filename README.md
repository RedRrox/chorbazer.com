<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>CHOR BAZER | PREMIUM TOP UP</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;800&family=Rajdhani:wght@500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --neon-green: #00ff88;
            --neon-yellow: #ccff00;
            --dark-bg: #030303;
            --card-bg: rgba(20, 20, 20, 0.95);
            --border-color: rgba(255, 255, 255, 0.08);
            --bkash-color: #d12053;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Rajdhani', sans-serif; -webkit-tap-highlight-color: transparent; }
        body { background: var(--dark-bg); color: #f0f0f0; overflow-x: hidden; width: 100%; }

        header { background: #000; padding: 15px 0; text-align: center; border-bottom: 1px solid var(--border-color); position: sticky; top: 0; z-index: 100; }
        .logo { font-family: 'Orbitron', sans-serif; font-size: clamp(1.2rem, 5vw, 1.8rem); color: var(--neon-yellow); letter-spacing: 3px; margin-bottom: 10px; }
        
        nav { display: flex; justify-content: center; gap: 10px; margin-top: 10px; }
        .nav-btn {
            background: rgba(255, 255, 255, 0.05); border: 1px solid var(--border-color);
            color: #fff; padding: 6px 15px; border-radius: 5px; font-size: 13px; cursor: pointer;
            transition: 0.3s;
        }
        .nav-btn:hover { background: var(--neon-yellow); color: #000; transform: translateX(3px); }

        .page { display: none; width: 95%; max-width: 450px; margin: 10px auto; animation: fadeIn 0.4s; }
        .page.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        #notify-box { 
            background: rgba(255, 255, 255, 0.03); border: 1px solid rgba(255, 255, 255, 0.1); 
            padding: 10px; border-radius: 8px; margin-bottom: 15px; text-align: center; 
            font-weight: bold; color: var(--neon-green); font-size: 13px;
        }

        .box { background: var(--card-bg); border: 1px solid var(--border-color); padding: 15px; border-radius: 12px; margin-bottom: 12px; }
        h2 { font-size: 14px; margin-bottom: 12px; color: var(--neon-yellow); text-transform: uppercase; border-left: 3px solid var(--neon-yellow); padding-left: 8px; }

        input[type="text"] { width: 100%; padding: 12px; background: #000; border: 1px solid #333; color: var(--neon-yellow); border-radius: 8px; text-align: center; font-weight: bold; outline: none; }

        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
        .item { background: rgba(0,0,0,0.5); border: 1px solid var(--border-color); padding: 15px; border-radius: 10px; text-align: center; cursor: pointer; position: relative; }
        .item.active { border-color: var(--neon-green); background: rgba(0, 255, 136, 0.05); }
        .price { color: var(--neon-green); font-weight: bold; font-size: 18px; display: block; }

        /* Special Pack UI */
        .special-badge { position: absolute; top: 0; left: 0; background: #ff4444; color: #fff; font-size: 8px; font-weight: 800; padding: 2px 8px; border-radius: 0 0 8px 0; }
        .premium-card { grid-column: span 2; border: 1px solid #ff4444 !important; opacity: 0.8; cursor: not-allowed; }
        .stock-tag { background: #ff4444; color: #fff; font-size: 9px; padding: 1px 6px; border-radius: 4px; margin-top: 4px; display: inline-block; }

        .btn-buy { width: 100%; padding: 14px; background: var(--neon-yellow); color: #000; border: none; border-radius: 8px; font-weight: bold; cursor: pointer; margin-top: 10px; text-transform: uppercase; }

        /* --- bKash Modal --- */
        #bkash-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 1000; justify-content: center; align-items: center; }
        .bkash-content { background: #fff; width: 92%; max-width: 340px; border-radius: 12px; overflow: hidden; color: #333; padding-bottom: 12px; }
        .bkash-header { padding: 8px; text-align: center; border-bottom: 1px solid #eee; }
        .bkash-header img { width: 70px; }
        .bkash-main-body { background: #d12053; color: #fff; padding: 12px; margin: 0 10px; border-radius: 8px; text-align: center; }
        .bkash-steps { text-align: left; font-size: 11px; line-height: 1.5; border-top: 1px solid rgba(255,255,255,0.2); padding-top: 10px; margin-top: 10px; }
        .verify-red-btn { width: 90%; margin: 10px auto 0; display: block; padding: 12px; background: #d00000; color: #fff; border: none; font-weight: bold; cursor: pointer; border-radius: 4px; }

        /* Success Popup */
        #success-popup { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.95); z-index: 2000; justify-content: center; align-items: center; }
        .success-card { background: #111; border: 1px solid var(--neon-green); width: 85%; max-width: 300px; padding: 30px; border-radius: 20px; text-align: center; }

        footer { text-align: center; padding: 25px 10px; border-top: 1px solid var(--border-color); font-size: 10px; background: #000; }
        .glow-text { color: var(--neon-green); text-shadow: 0 0 8px rgba(0, 255, 136, 0.6); font-weight: bold; }
    </style>
</head>
<body onload="startOrderHistory()">

<header>
    <div class="logo">CHOR BAZER</div>
    <nav>
        <button class="nav-btn" onclick="showPage('home')">Home</button>
        <button class="nav-btn" onclick="showPage('about')">About</button>
        <button class="nav-btn" onclick="showPage('contact')">Contact</button>
    </nav>
</header>

<div id="home" class="page active">
    <div id="notify-box">🚀 Secure Top-Up Active</div>
    <div class="box">
        <h2>1. Player UID</h2>
        <input type="text" id="uid-input" placeholder="Enter Player UID here">
    </div>
    <div class="box">
        <h2>2. Select Pack</h2>
        <div class="grid">
            <div class="item premium-card">
                <div class="special-badge">LIMITED TIME</div>
                <span style="font-weight:700;">💎 2x Monthly Member 💎</span>
                <span class="price" style="opacity: 0.5;">৳ 1</span>
                <span class="stock-tag">OUT OF STOCK</span>
            </div>
            <div class="item" onclick="selectPack(this, 'Weekly Member', 140)">
                <span>Weekly Member</span><span class="price">৳ 140</span>
            </div>
            <div class="item" onclick="selectPack(this, 'Monthly Member', 650)">
                <span>Monthly Member</span><span class="price">৳ 650</span>
            </div>
        </div>
    </div>
    <div class="box">
        <div style="color:var(--neon-green); font-size:20px; font-weight:bold;">Total: ৳ <span id="sum-total">0</span></div>
        <button class="btn-buy" onclick="openPayment()">BUY NOW</button>
    </div>
</div>

<div id="about" class="page">
    <div class="box">
        <h2>About Chor Bazer</h2>
        <p style="color:#ccc; line-height:1.6;">Welcome to <b>Chor Bazer</b>, the most trusted gaming top-up platform in Bangladesh. We provide Free Fire Membership and Diamonds with speed and security.</p>
        <p style="color:#ccc; margin-top:10px;">✅ Fast Delivery<br>✅ 24/7 Support</p>
    </div>
</div>

<div id="contact" class="page">
    <div class="box">
        <h2>Contact Us</h2>
        <button style="width:100%; padding:12px; background:#0088cc; color:#fff; border:none; border-radius:8px; font-weight:bold;">Message on WhatsApp</button>
        <p style="text-align:center; font-size:12px; margin-top:15px; color:#666;">Email: support@chorbazer.com</p>
    </div>
</div>

<div id="bkash-modal">
    <div class="bkash-content">
        <div class="bkash-header"><img src="bikashlogo.png" alt="bkash"></div>
        <div class="bkash-main-body">
            <h3>ট্রান্সজেকশন আইডি দিন</h3>
            <input type="text" id="trx-input" style="width:100%; padding:8px; border-radius:4px; border:none; margin:10px 0; text-align:center; font-weight:bold;">
            <div class="bkash-steps">
                <p>● <b>"Send Money"</b> করুনঃ <b>01779772201</b> <button onclick="copyNum()" style="padding:1px 5px; font-size:9px;">Copy</button></p>
                <p>● টাকার পরিমাণঃ ৳ <b id="pay-amount">0</b></p>
                <p>● পেমেন্ট শেষে TrxID টি উপরে বসিয়ে ভেরিফাই করুন।</p>
            </div>
        </div>
        <button class="verify-red-btn" onclick="verifyOrder()">VERIFY</button>
        <button onclick="document.getElementById('bkash-modal').style.display='none'" style="width:100%; background:none; border:none; color:#999; font-size:10px; margin-top:5px;">CANCEL</button>
    </div>
</div>

<div id="success-popup">
    <div class="success-card">
        <h2 style="color:var(--neon-green)">ORDER SUCCESS!</h2>
        <p style="color:#aaa; margin:15px 0;">Processing your delivery...</p>
        <button onclick="closeSuccess()" style="padding:10px 25px; background:var(--neon-green); color:#000; border:none; border-radius:5px; font-weight:bold;">CLOSE</button>
    </div>
</div>

<footer>
    © 2026 <span class="glow-text">CHOR BAZER</span> | POWERED BY <span class="glow-text">RRX STUDIOS</span>
</footer>

<script>
    let selectedPrice = 0;
    let selectedPack = "";

    function showPage(p) {
        document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
        document.getElementById(p).classList.add('active');
    }

    function selectPack(el, name, price) {
        if(el.classList.contains('premium-card')) return;
        document.querySelectorAll('.item').forEach(i => i.classList.remove('active'));
        el.classList.add('active');
        selectedPrice = price; selectedPack = name;
        document.getElementById('sum-total').innerText = price;
        document.getElementById('pay-amount').innerText = price;
    }

    function openPayment() {
        const uid = document.getElementById('uid-input').value;
        if(!selectedPrice || !uid) return alert("UID ও প্যাক সিলেক্ট করুন!");
        document.getElementById('bkash-modal').style.display = 'flex';
    }

    function verifyOrder() {
        const trx = document.getElementById('trx-input').value;
        if(trx.length < 5) return alert("Invalid TrxID!");
        
        document.getElementById('bkash-modal').style.display = 'none';
        document.getElementById('success-popup').style.display = 'flex';
        
        const notify = document.getElementById('notify-box');
        const uid = document.getElementById('uid-input').value;
        notify.innerHTML = `<span style="color:var(--neon-green)">🔥 SUCCESS! ${uid} just bought ${selectedPack}.</span>`;
    }

    function closeSuccess() {
        document.getElementById('success-popup').style.display = 'none';
        location.reload();
    }

    function copyNum() { navigator.clipboard.writeText("01779772201"); alert("Copied!"); }

    function startOrderHistory() {
        const fakes = ["UID 4521***", "UID 9982***", "UID 1025***", "UID 7741***", "UID 3025***"];
