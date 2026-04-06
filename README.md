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
            --gold: #ffd700;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Rajdhani', sans-serif; }
        body { background: var(--dark-bg); color: #fff; padding-bottom: 50px; }

        header { background: #000; padding: 25px; text-align: center; border-bottom: 2px solid var(--neon-yellow); box-shadow: 0 0 20px rgba(204, 255, 0, 0.2); }
        .logo { font-family: 'Orbitron', sans-serif; font-size: 35px; color: var(--neon-yellow); letter-spacing: 5px; }

        .container { max-width: 600px; margin: 20px auto; padding: 15px; }

        #notify-box { 
            background: rgba(204, 255, 0, 0.05); 
            border: 1px dashed var(--neon-yellow); 
            padding: 12px; border-radius: 8px; margin-bottom: 20px; 
            text-align: center; font-weight: bold; color: var(--neon-yellow); font-size: 14px;
        }

        .box { background: var(--card-bg); border: 1px solid #222; padding: 20px; border-radius: 12px; margin-bottom: 20px; }
        h2 { font-size: 18px; margin-bottom: 15px; color: var(--neon-yellow); text-transform: uppercase; border-left: 4px solid var(--neon-yellow); padding-left: 10px; }

        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .item { background: #000; border: 1px solid #222; padding: 20px; border-radius: 10px; cursor: pointer; text-align: center; transition: 0.3s; position: relative; }
        .item.active { border-color: var(--neon-yellow); background: rgba(204, 255, 0, 0.08); }
        .item .price { color: var(--neon-yellow); font-weight: bold; font-size: 22px; display: block; }

        /* --- Premium Special Card --- */
        .premium-card {
            grid-column: span 2; /* পুরা জায়গা জুড়ে থাকবে */
            background: linear-gradient(145deg, #1a1a1a, #000);
            border: 2px solid var(--gold) !important;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.3);
            overflow: hidden;
            cursor: not-allowed !important;
        }
        .premium-card::before {
            content: "LIMITED OFFER";
            position: absolute;
            top: 10px;
            right: -30px;
            background: var(--gold);
            color: #000;
            font-size: 10px;
            font-weight: bold;
            padding: 5px 40px;
            transform: rotate(45deg);
        }
        .premium-card .price { color: var(--gold) !important; text-decoration: line-through; opacity: 0.6; }
        .premium-card .stock-tag {
            background: #ff4444;
            color: #fff;
            font-size: 12px;
            padding: 4px 12px;
            border-radius: 4px;
            display: inline-block;
            margin-top: 8px;
            font-weight: 800;
        }

        .summary p { display: flex; justify-content: space-between; margin-bottom: 8px; color: #aaa; }
        .total { color: var(--neon-yellow); font-size: 24px; font-weight: bold; border-top: 1px solid #333; padding-top: 10px; margin-top: 10px; }
        .btn-buy { width: 100%; padding: 18px; background: var(--neon-yellow); color: #000; border: none; border-radius: 8px; font-weight: bold; font-size: 20px; cursor: pointer; margin-top: 10px; }

        /* bKash Modal */
        #bkash-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 9999; justify-content: center; align-items: center; }
        .bkash-content { background: #fff; width: 92%; max-width: 400px; border-radius: 12px; overflow: hidden; color: #000; }
        .bkash-body { background: var(--bkash-color); color: #fff; padding: 20px; }
        .trx-input { width: 100%; padding: 14px; margin: 10px 0; border-radius: 6px; border: none; font-size: 18px; text-align: center; font-weight: bold; }
        .verify-btn { width: 90%; margin: 15px auto; display: block; padding: 15px; background: #d00000; color: #fff; border: none; font-weight: bold; border-radius: 8px; }
    </style>
</head>
<body>

<header><div class="logo">CHOR BAZER</div></header>

<div class="container">
    <div id="notify-box">🚀 Loading Secure Top-Up Server...</div>

    <div class="box">
        <h2>1. Player UID / Roblox Username</h2>
        <input type="text" id="uid-input" placeholder="Enter UID or Username" oninput="updateID()">
    </div>

    <div class="box">
        <h2>2. Select Pack</h2>
        <div class="grid">
            <div class="item premium-card">
                <span style="color:var(--gold); font-weight:800; font-size:18px;">💎 2x Monthly Member 💎</span>
                <span class="price">৳ 1</span>
                <span class="stock-tag">OUT OF STOCK</span>
            </div>

            <div class="item" onclick="selectPack(this, 'Weekly Member', 140)">
                <span>Weekly Member</span>
                <span class="price">৳ 140</span>
            </div>
            <div class="item" onclick="selectPack(this, 'Monthly Member', 650)">
                <span>Monthly Member</span>
                <span class="price">৳ 650</span>
            </div>
            <div class="item" onclick="selectPack(this, '40 Robux', 50)">
                <span>40 Robux</span>
                <span class="price">৳ 50</span>
            </div>
            <div class="item" onclick="selectPack(this, '400 Robux', 500)">
                <span>400 Robux</span>
                <span class="price">৳ 500</span>
            </div>
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
        <div style="text-align:center; padding:15px; border-bottom:1px solid #eee;"><img src="bikashlogo.png" width="100"></div>
        <div class="bkash-body">
            <p style="text-align: center; font-weight: bold; margin-bottom: 15px;">ট্রানজেকশন আইডি দিন</p>
            <input type="text" class="trx-input" id="trx-input" placeholder="TrxID এখানে দিন">
            <div style="font-size:13px; margin-bottom:8px;">● নম্বরঃ <b>01779772201</b> <button onclick="copyNum()" style="background:#fff; border:none; padding:2px 5px; border-radius:3px; font-size:10px; cursor:pointer; font-weight:bold;">COPY</button></div>
            <div style="font-size:13px;">● টাকার পরিমাণঃ ৳ <b id="pay-amount">0</b></div>
        </div>
        <button class="verify-btn" onclick="verifyRealOrder()">VERIFY</button>
        <button onclick="document.getElementById('bkash-modal').style.display='none'" style="width: 100%; background: #f5f5f5; border: none; padding: 12px; cursor: pointer;">CANCEL</button>
    </div>
</div>

<script>
    let selectedPrice = 0;
    let selectedPackName = "";
    let notifyInterval;

    const fakeFF = ["ID 4521***", "ID 9982***", "ID 1002***", "ID 7745***"];
    const fakeRobux = ["user rafi***", "user sakib***", "user king***", "user topup_pro***"];

    function startFakeNotifications() {
        notifyInterval = setInterval(() => {
            const notify = document.getElementById('notify-box');
            notify.style.opacity = '0';
            setTimeout(() => {
                const isRobux = Math.random() > 0.5;
                if(isRobux) {
                    const user = fakeRobux[Math.floor(Math.random() * fakeRobux.length)];
                    notify.innerText = `Success! ${user} got 40 Robux.`;
                } else {
                    const id = fakeFF[Math.floor(Math.random() * fakeFF.length)];
                    notify.innerText = `${id} just bought Weekly!`;
                }
                notify.style.opacity = '1';
            }, 500);
        }, 10000);
    }

    function verifyRealOrder() {
        const trx = document.getElementById('trx-input').value;
        const uid = document.getElementById('uid-input').value;
        if(trx.length < 5) { alert("ভুল ট্রানজেকশন আইডি!"); return; }

        clearInterval(notifyInterval);
        const notify = document.getElementById('notify-box');
        notify.innerHTML = `<span style="color:#00ff88">✅ ORDER DONE! ${uid} just purchased ${selectedPackName}.</span>`;
        alert("অর্ডার সফল! ৩০-৪০ মিনিটের মধ্যে ডেলিভারি পাবেন।");
        document.getElementById('bkash-modal').style.display = 'none';
        setTimeout(() => { startFakeNotifications(); }, 15000);
    }

    startFakeNotifications();

    function selectPack(el, name, price) {
        // আউট অফ স্টকে ক্লিক করলে কাজ করবে না
        if(el.classList.contains('premium-card')) return; 

        document.querySelectorAll('.item').forEach(i => i.classList.remove('active'));
        el.classList.add('active');
        selectedPrice = price;
        selectedPackName = name;
        document.getElementById('sum-pack').innerText = name;
        document.getElementById('sum-total').innerText = price;
        document.getElementById('pay-amount').innerText = price;
    }

    function updateID() { document.getElementById('sum-id').innerText = document.getElementById('uid-input').value || "-"; }
    function openPayment() { if(!document.getElementById('uid-input').value || selectedPrice === 0) { alert("তথ্য দিন!"); return; } document.getElementById('bkash-modal').style.display = 'flex'; }
    function copyNum() { navigator.clipboard.writeText("01779772201"); alert("Number Copied!"); }
</script>

</body>
</html>
