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
            --gold: #ffd700;
        }

        /* Mobile Optimization Fixes */
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Rajdhani', sans-serif; -webkit-tap-highlight-color: transparent; }
        body { background: var(--dark-bg); color: #f0f0f0; line-height: 1.4; overflow-x: hidden; width: 100%; }

        header { background: #000; padding: 15px 0; text-align: center; border-bottom: 1px solid var(--border-color); position: sticky; top: 0; z-index: 100; }
        .logo { font-family: 'Orbitron', sans-serif; font-size: clamp(1.2rem, 5vw, 1.8rem); color: var(--neon-yellow); letter-spacing: 3px; }

        .container { width: 95%; max-width: 450px; margin: 10px auto; padding-bottom: 20px; }

        #notify-box { 
            background: rgba(255, 255, 255, 0.03); border: 1px solid rgba(255, 255, 255, 0.1); 
            padding: 10px; border-radius: 8px; margin-bottom: 15px; text-align: center; 
            font-weight: bold; color: var(--neon-green); font-size: 13px;
        }

        .box { background: var(--card-bg); border: 1px solid var(--border-color); padding: 15px; border-radius: 12px; margin-bottom: 12px; }
        h2 { font-size: 14px; margin-bottom: 12px; color: var(--neon-yellow); text-transform: uppercase; border-left: 3px solid var(--neon-yellow); padding-left: 8px; }

        input[type="text"] { 
            width: 100%; padding: 12px; background: #000; border: 1px solid #333; 
            color: var(--neon-yellow); border-radius: 8px; font-size: 16px; outline: none; text-align: center; font-weight: bold;
        }

        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
        .item { 
            background: rgba(0,0,0,0.5); border: 1px solid var(--border-color); padding: 15px; 
            border-radius: 10px; cursor: pointer; text-align: center; position: relative; overflow: hidden;
        }
        .item.active { border-color: var(--neon-green); background: rgba(0, 255, 136, 0.05); }
        .item span { font-size: 12px; color: #999; }
        .item .price { color: var(--neon-green); font-weight: bold; font-size: 18px; display: block; }

        .special-badge { position: absolute; top: 0; left: 0; background: #ff4444; color: #fff; font-size: 8px; font-weight: 800; padding: 2px 8px; border-radius: 0 0 8px 0; }
        .premium-card { grid-column: span 2; border: 1px solid #ff4444 !important; opacity: 0.8; }
        .stock-tag { background: #ff4444; color: #fff; font-size: 9px; padding: 1px 6px; border-radius: 4px; margin-top: 4px; display: inline-block; }

        .summary p { display: flex; justify-content: space-between; margin-bottom: 6px; color: #aaa; font-size: 13px; }
        .total { color: var(--neon-green); font-size: 20px; font-weight: bold; border-top: 1px solid #222; padding-top: 8px; margin-top: 8px; }
        .btn-buy { width: 100%; padding: 14px; background: var(--neon-yellow); color: #000; border: none; border-radius: 8px; font-weight: bold; font-size: 16px; cursor: pointer; margin-top: 8px; text-transform: uppercase; }

        /* --- Compact & Mobile Optimized bKash Modal --- */
        #bkash-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 1000; justify-content: center; align-items: center; }
        .bkash-content { background: #fff; width: 92%; max-width: 340px; border-radius: 12px; overflow: hidden; color: #333; padding-bottom: 12px; position: relative; }
        
        .bkash-header { padding: 8px; text-align: center; border-bottom: 1px solid #eee; }
        .bkash-header img { width: 70px; }

        .bkash-main-body { background: #d12053; color: #fff; padding: 12px; margin: 0 10px; border-radius: 8px; text-align: center; }
        .bkash-main-body h3 { font-size: 14px; margin-bottom: 10px; font-weight: 600; }
        .trx-input-box { width: 100%; padding: 8px; border-radius: 4px; border: none; margin-bottom: 12px; font-size: 15px; text-align: center; color: #000; }

        .bkash-steps { text-align: left; font-size: 11px; line-height: 1.5; border-top: 1px solid rgba(255,255,255,0.2); padding-top: 10px; }
        .bkash-steps p { margin-bottom: 6px; padding-left: 10px; position: relative; }
        .bkash-steps p::before { content: "•"; position: absolute; left: 0; color: #fff; }

        .copy-btn-bkash { background: #fff; color: #000; border: none; padding: 1px 5px; border-radius: 3px; font-size: 9px; cursor: pointer; font-weight: bold; margin-left: 4px; }
        .verify-red-btn { width: 90%; margin: 10px auto 0; display: block; padding: 12px; background: #d00000; color: #fff; border: none; font-weight: bold; cursor: pointer; font-size: 14px; border-radius: 4px; }

        /* --- Glowing Footer --- */
        footer { 
            text-align: center; padding: 25px 10px; margin-top: 20px; border-top: 1px solid var(--border-color); 
            font-size: 10px; color: #666; background: #000; letter-spacing: 1px;
        }
        .glow-text { 
            color: var(--neon-green); 
            text-shadow: 0 0 8px rgba(0, 255, 136, 0.6); 
            font-weight: bold;
        }

        /* Prevent Auto-Zoom on Input */
        @media screen and (max-width: 768px) {
            input[type="text"] { font-size: 16px; }
        }
    </style>
</head>
<body>

<header><div class="logo">CHOR BAZER</div></header>

<div class="container">
    <div id="notify-box">🚀 Loading Secure Connection...</div>

    <div class="box">
        <h2>1. Player UID</h2>
        <input type="text" id="uid-input" placeholder="Enter UID here" oninput="updateID()">
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

    <div class="box summary">
        <h2>3. Order Summary</h2>
        <p>Selected Pack: <span id="sum-pack">-</span></p>
        <p>Player UID: <span id="sum-id">-</span></p>
        <div class="total">Total: ৳ <span id="sum-total">0</span></div>
        <button class="btn-buy" onclick="openPayment()">BUY NOW</button>
    </div>
</div>

<div id="bkash-modal">
    <div class="bkash-content">
        <div class="bkash-header"><img src="bikashlogo.png" alt="bkash"></div>
        <div class="bkash-main-body">
            <h3>ট্রান্সজেকশন আইডি দিন</h3>
            <input type="text" class="trx-input-box" id="trx-input">
            <div class="bkash-steps">
                <p>*247# ডায়াল করে আপনার bKash মোবাইল মেনুতে যান অথবা bKash অ্যাপে যান।</p>
                <p><b>"Send Money"</b> -এ ক্লিক করুন।</p>
                <p>প্রাপক নম্বর হিসেবে এই নম্বরটি লিখুনঃ <b>01779772201</b> <button class="copy-btn-bkash" onclick="copyNum()">Copy</button></p>
                <p>টাকার পরিমাণঃ <b id="pay-amount">0</b></p>
                <p>নিশ্চিত করতে এখন আপনার bKash মোবাইল মেনু পিন লিখুন।</p>
                <p>সবকিছু ঠিক থাকলে, আপনি bKash থেকে একটি নিশ্চিতকরণ বার্তা পাবেন।</p>
                <p>এখন উপরের বক্সে আপনার <b>Transaction ID</b> দিন এবং নিচের <b>VERIFY</b> বাটনে ক্লিক করুন।</p>
            </div>
        </div>
        <button class="verify-red-btn" onclick="verifyRealOrder()">VERIFY</button>
        <button onclick="document.getElementById('bkash-modal').style.display='none'" style="width: 100%; background: none; border: none; padding: 10px; cursor: pointer; color: #999; font-size: 10px;">CANCEL</button>
    </div>
</div>

<footer>
    © 2026 <span class="glow-text">CHOR BAZER</span> | POWERED BY <span class="glow-text">RRX STUDIOS</span>
</footer>

<script>
    let selectedPrice = 0;
    let selectedPackName = "";
    let notifyInterval;

    const fakeFF = ["UID 4521***", "UID 9982***", "UID 1002***", "UID 7745***", "UID 1025***"];
    function startFake() {
        notifyInterval = setInterval(() => {
            const notify = document.getElementById('notify-box');
            notify.style.opacity = '0';
            setTimeout(() => {
                notify.innerText = `✅ ${fakeFF[Math.floor(Math.random() * fakeFF.length)]} just bought ${Math.random() > 0.5 ? 'Weekly' : 'Monthly'}!`;
                notify.style.opacity = '1';
            }, 500);
        }, 10000);
    }

    function verifyRealOrder() {
        if(document.getElementById('trx-input').value.trim().length < 5) return alert("ভুল ট্রানজেকশন আইডি!");
        clearInterval(notifyInterval);
        document.getElementById('notify-box').innerHTML = `<span style="color:var(--neon-green)">✅ ORDER DONE! ${document.getElementById('uid-input').value} just purchased ${selectedPackName}.</span>`;
        alert("অর্ডার সফল! ৩০-৪০ মিনিটের মধ্যে ডেলিভারি পাবেন।");
        document.getElementById('bkash-modal').style.display = 'none';
        setTimeout(startFake, 15000);
    }

    function selectPack(el, name, price) {
        if(el.classList.contains('premium-card')) return;
        document.querySelectorAll('.item').forEach(i => i.classList.remove('active'));
        el.classList.add('active');
        selectedPrice = price; selectedPackName = name;
        document.getElementById('sum-pack').innerText = name;
        document.getElementById('sum-total').innerText = price;
        document.getElementById('pay-amount').innerText = price;
    }

    function updateID() { document.getElementById('sum-id').innerText = document.getElementById('uid-input').value || "-"; }
    function openPayment() { if(!selectedPrice) return alert("প্যাক সিলেক্ট করুন!"); document.getElementById('bkash-modal').style.display = 'flex'; }
    function copyNum() { navigator.clipboard.writeText("01779772201"); alert("নম্বর কপি হয়েছে!"); }

    startFake();
</script>

</body>
</html>
