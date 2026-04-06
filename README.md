<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CHOR BAZER | GAME TOP UP</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;800&family=Rajdhani:wght@500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --neon-yellow: #ccff00;
            --dark-bg: #0a0a0a;
            --card-bg: #151515;
            --bkash-color: #d12053;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Rajdhani', sans-serif; }
        body { background: var(--dark-bg); color: #fff; padding-bottom: 50px; }

        header { background: #000; padding: 25px; text-align: center; border-bottom: 2px solid var(--neon-yellow); box-shadow: 0 0 20px rgba(204, 255, 0, 0.2); }
        .logo { font-family: 'Orbitron', sans-serif; font-size: 35px; color: var(--neon-yellow); letter-spacing: 5px; }

        .container { max-width: 600px; margin: 20px auto; padding: 15px; }

        /* Notification Box */
        #notify-box { 
            background: rgba(204, 255, 0, 0.05); 
            border: 1px dashed var(--neon-yellow); 
            padding: 12px; 
            border-radius: 8px; 
            margin-bottom: 20px; 
            text-align: center; 
            font-weight: bold; 
            color: var(--neon-yellow); 
            font-size: 14px;
            min-height: 45px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.5s ease;
        }

        .real-order { color: #00ff88 !important; border-color: #00ff88 !important; background: rgba(0, 255, 136, 0.1) !important; animation: highlight 1s ease; }
        @keyframes highlight { 0% {transform: scale(1);} 50% {transform: scale(1.05);} 100% {transform: scale(1);} }

        .box { background: var(--card-bg); border: 1px solid #222; padding: 20px; border-radius: 12px; margin-bottom: 20px; }
        h2 { font-size: 18px; margin-bottom: 15px; color: var(--neon-yellow); text-transform: uppercase; border-left: 4px solid var(--neon-yellow); padding-left: 10px; }

        input[type="text"] { width: 100%; padding: 15px; background: #000; border: 1px solid #333; color: var(--neon-yellow); border-radius: 8px; font-size: 18px; outline: none; text-align: center; font-weight: bold; }

        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .item { background: #000; border: 1px solid #222; padding: 20px; border-radius: 10px; cursor: pointer; text-align: center; transition: 0.3s; }
        .item.active { border-color: var(--neon-yellow); background: rgba(204, 255, 0, 0.08); }
        .item .price { color: var(--neon-yellow); font-weight: bold; font-size: 22px; display: block; }

        .summary p { display: flex; justify-content: space-between; margin-bottom: 8px; color: #aaa; }
        .summary .total { color: var(--neon-yellow); font-size: 24px; font-weight: bold; border-top: 1px solid #333; padding-top: 10px; margin-top: 10px; }

        .btn-buy { width: 100%; padding: 18px; background: var(--neon-yellow); color: #000; border: none; border-radius: 8px; font-weight: bold; font-size: 20px; cursor: pointer; margin-top: 10px; }

        /* Modal */
        #bkash-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 9999; justify-content: center; align-items: center; }
        .bkash-content { background: #fff; width: 92%; max-width: 400px; border-radius: 12px; overflow: hidden; color: #000; text-align: center; }
        .bkash-body { background: var(--bkash-color); color: #fff; padding: 20px; text-align: left; }
        .copy-btn { background: #fff; color: #000; border: none; padding: 2px 8px; border-radius: 4px; font-size: 10px; cursor: pointer; margin-left: 10px; font-weight: bold; }
        .verify-btn { width: 90%; margin: 15px auto; display: block; padding: 15px; background: #d00000; color: #fff; border: none; font-weight: bold; cursor: pointer; border-radius: 8px; }
    </style>
</head>
<body>

<header>
    <div class="logo">CHOR BAZER</div>
</header>

<div class="container">
    <div id="notify-box">🚀 Initializing Chor Bazer secure server...</div>

    <div class="box">
        <h2>1. Player UID / Roblox Username</h2>
        <input type="text" id="uid-input" placeholder="Enter UID or Username" oninput="updateSummary()">
    </div>

    <div class="box">
        <h2>2. Select Pack</h2>
        <div class="grid">
            <div class="item" onclick="selectPack(this, 'Weekly Member', 140)"><span>Weekly Member</span><span class="price">৳ 140</span></div>
            <div class="item" onclick="selectPack(this, 'Monthly Member', 650)"><span>Monthly Member</span><span class="price">৳ 650</span></div>
            <div class="item" onclick="selectPack(this, '40 Robux', 50)"><span>40 Robux</span><span class="price">৳ 50</span></div>
            <div class="item" onclick="selectPack(this, '400 Robux', 500)"><span>400 Robux</span><span class="price">৳ 500</span></div>
        </div>
    </div>

    <div class="box summary">
        <h2>3. Order Summary</h2>
        <p>Selected: <span id="sum-pack">-</span></p>
        <p>ID/Username: <span id="sum-id">-</span></p>
        <div class="total">Total: ৳ <span id="sum-total">0</span></div>
        <button class="btn-buy" onclick="openPayment()">BUY NOW</button>
    </div>
</div>

<div id="bkash-modal">
    <div class="bkash-content">
        <div style="padding:15px; border-bottom:1px solid #eee;"><img src="bikashlogo.png" width="100"></div>
        <div class="bkash-body">
            <p style="text-align: center; font-weight: bold; margin-bottom: 15px;">পেমেন্ট ভেরিফাই করুন</p>
            <input type="text" id="trx-input" style="width:100%; padding:14px; border-radius:6px; border:none; font-size:18px; text-align:center; margin-bottom:15px;" placeholder="TrxID এখানে দিন">
            <div style="font-size:13px; margin-bottom:8px;">● নম্বরঃ <b>01779772201</b> <button class="copy-btn" onclick="copyNum()">COPY</button></div>
            <div style="font-size:13px;">● টাকার পরিমাণঃ ৳ <b id="pay-amount">0</b></div>
        </div>
        <button class="verify-btn" onclick="processRealOrder()">VERIFY ORDER</button>
        <button onclick="document.getElementById('bkash-modal').style.display='none'" style="width: 100%; background: #f5f5f5; border: none; padding: 12px; color: #666; font-weight: bold; cursor:pointer;">CANCEL</button>
    </div>
</div>

<script>
    let selectedPrice = 0;
    let selectedPackName = "";
    let notifyInterval;

    // ফেক ডাটা
    const ffNames = ["ID 4521***", "ID 9982***", "ID 1002***", "ID 7745***"];
    const robloxUsers = ["user rafi***", "user sakib***", "user op_gamer***", "user king***"];

    function showFakeNotification() {
        const notify = document.getElementById('notify-box');
        notify.classList.remove('real-order');
        notify.style.opacity = '0';
        
        setTimeout(() => {
            const isRobux = Math.random() > 0.5;
            if (isRobux) {
                const user = robloxUsers[Math.floor(Math.random() * robloxUsers.length)];
                notify.innerText = `Success! ${user} got 40 Robux.`;
            } else {
                const id = ffNames[Math.floor(Math.random() * ffNames.length)];
                notify.innerText = `${id} just bought Weekly!`;
            }
            notify.style.opacity = '1';
        }, 500);
    }

    // অটো ফেক নোটিফিকেশন শুরু
    notifyInterval = setInterval(showFakeNotification, 10000);
    showFakeNotification();

    // আসল অর্ডার প্রসেসিং লজিক
    function processRealOrder() {
        const trx = document.getElementById('trx-input').value;
        const uid = document.getElementById('uid-input').value;

        if(trx.length < 5) {
            alert("TrxID সঠিক নয়!");
            return;
        }

        // আসল অর্ডারের ইনফো নোটিফিকেশনে সেট করা
        clearInterval(notifyInterval); // ফেক নোটিফিকেশন থামানো
        const notify = document.getElementById('notify-box');
        
        notify.classList.add('real-order');
        notify.innerText = `✅ ORDER DONE! ${uid} just purchased ${selectedPackName}.`;

        alert("অর্ডার সফল! আপনার প্যাকটি ৩০-৪০ মিনিটে পৌঁছে যাবে।");
        
        document.getElementById('bkash-modal').style.display = 'none';

        // ১০ সেকেন্ড পর আবার ফেক নোটিফিকেশন শুরু করা
        setTimeout(() => {
            notifyInterval = setInterval(showFakeNotification, 10000);
        }, 10000);
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

    function updateSummary() {
        document.getElementById('sum-id').innerText = document.getElementById('uid-input').value || "-";
    }

    function openPayment() {
        if(!document.getElementById('uid-input').value || selectedPrice === 0) {
            alert("সব তথ্য পূরণ করুন!");
            return;
        }
        document.getElementById('bkash-modal').style.display = 'flex';
    }

    function copyNum() {
        navigator.clipboard.writeText("01779772201");
        alert("Number Copied!");
    }
</script>

</body>
</html>
