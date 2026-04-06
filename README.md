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
            --text-main: #ffffff;
            --input-bg: #000;
            --header-bg: #000;
            --notify-text: #ccff00;
        }

        .light-mode {
            --dark-bg: #ffffff;
            --card-bg: #f9f9f9;
            --text-main: #000000;
            --neon-yellow: #000000;
            --input-bg: #ffffff;
            --header-bg: #ffffff;
            --notify-text: #333333;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Rajdhani', sans-serif; transition: 0.3s; }
        body { background: var(--dark-bg); color: var(--text-main); padding-bottom: 50px; }

        header { 
            background: var(--header-bg); 
            padding: 25px; 
            text-align: center; 
            border-bottom: 2px solid var(--neon-yellow); 
            position: relative;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }
        .logo { font-family: 'Orbitron', sans-serif; font-size: 30px; color: var(--neon-yellow); letter-spacing: 5px; }

        #theme-toggle {
            position: absolute; right: 15px; top: 22px;
            background: var(--neon-yellow); border: none;
            padding: 8px 12px; border-radius: 20px; cursor: pointer;
            font-size: 18px; color: var(--header-bg); font-weight: bold;
        }

        .container { max-width: 600px; margin: 20px auto; padding: 15px; }

        #notify-box { 
            background: rgba(128, 128, 128, 0.1); 
            border: 1px dashed var(--neon-yellow); 
            padding: 12px; border-radius: 8px; margin-bottom: 20px; 
            text-align: center; font-weight: bold; color: var(--notify-text); font-size: 15px;
        }

        .box { background: var(--card-bg); border: 1px solid #33333322; padding: 20px; border-radius: 12px; margin-bottom: 20px; }
        h2 { font-size: 18px; margin-bottom: 15px; color: var(--neon-yellow); text-transform: uppercase; border-left: 4px solid var(--neon-yellow); padding-left: 10px; }

        input[type="text"] { 
            width: 100%; padding: 15px; background: var(--input-bg); 
            border: 1px solid #33333344; color: var(--text-main); 
            border-radius: 8px; font-size: 18px; outline: none; text-align: center; font-weight: bold; 
        }

        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .item { background: var(--input-bg); border: 1px solid #33333333; padding: 20px; border-radius: 10px; cursor: pointer; text-align: center; position: relative; }
        .item.active { border-color: var(--neon-yellow); background: rgba(204, 255, 0, 0.1); }
        .item .price { color: var(--neon-yellow); font-weight: bold; font-size: 22px; display: block; }

        /* Special Pack Fix */
        .premium-card { 
            grid-column: span 2; border: 2px solid var(--gold) !important; 
            background: rgba(255, 215, 0, 0.05); cursor: not-allowed !important;
        }
        .light-mode .premium-card { border-color: #b8860b !important; }
        .stock-tag { background: #ff4444; color: #fff; font-size: 10px; padding: 2px 8px; border-radius: 4px; margin-top: 5px; display: inline-block; }

        .summary p { display: flex; justify-content: space-between; margin-bottom: 8px; }
        .total { color: var(--neon-yellow); font-size: 24px; font-weight: bold; border-top: 1px solid #33333322; padding-top: 10px; margin-top: 10px; }
        
        .btn-buy { width: 100%; padding: 18px; background: var(--neon-yellow); color: var(--header-bg); border: none; border-radius: 8px; font-weight: bold; font-size: 20px; cursor: pointer; margin-top: 10px; }

        /* bKash Modal & Logo Fix */
        #bkash-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 9999; justify-content: center; align-items: center; }
        .bkash-content { background: #fff; width: 92%; max-width: 400px; border-radius: 12px; overflow: hidden; color: #000; }
        .bkash-header { background: #fff; padding: 10px; text-align: center; border-bottom: 1px solid #eee; display: flex; justify-content: center; height: 60px; }
        .bkash-header img { height: 100%; width: auto; object-fit: contain; } /* লোগো ফিক্স */
        .bkash-body { background: var(--bkash-color); color: #fff; padding: 20px; text-align: left; }
        .instr { font-size: 13px; margin-bottom: 10px; border-bottom: 1px solid rgba(255,255,255,0.2); padding-bottom: 8px; }
        .trx-input { width: 100%; padding: 14px; margin: 10px 0; border-radius: 6px; border: none; font-size: 18px; text-align: center; font-weight: bold; }
        .verify-btn { width: 90%; margin: 15px auto; display: block; padding: 15px; background: #d00000; color: #fff; border: none; font-weight: bold; cursor: pointer; border-radius: 8px; text-transform: uppercase; }
    </style>
</head>
<body>

<header>
    <div class="logo">CHOR BAZER</div>
    <button id="theme-toggle" onclick="toggleTheme()">☀️</button>
</header>

<div class="container">
    <div id="notify-box">🚀 System Online...</div>

    <div class="box">
        <h2>1. Player UID / Roblox Username</h2>
        <input type="text" id="uid-input" placeholder="Enter UID or Username" oninput="updateID()">
    </div>

    <div class="box">
        <h2>2. Select Pack</h2>
        <div class="grid">
            <div class="item premium-card">
                <span style="color:var(--gold); font-weight:800;">💎 2x Monthly Member 💎</span>
                <span class="price" style="text-decoration: line-through; opacity: 0.5;">৳ 1</span>
                <span class="stock-tag">OUT OF STOCK</span>
            </div>
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
        <div class="bkash-header"><img src="bikashlogo.png" alt="bkash"></div>
        <div class="bkash-body">
            <p style="text-align: center; font-weight: bold; margin-bottom: 10px;">ট্রানজেকশন আইডি দিন</p>
            <input type="text" class="trx-input" id="trx-input" placeholder="TrxID">
            <div class="instr">● নম্বরঃ <b>01779772201</b> <button onclick="copyNum()" style="background:#fff; border:none; padding:2px 5px; border-radius:3px; font-size:10px; cursor:pointer;">COPY</button></div>
            <div class="instr">● টাকার পরিমাণঃ ৳ <b id="pay-amount">0</b></div>
        </div>
        <button class="verify-btn" onclick="verifyRealOrder()">VERIFY</button>
        <button onclick="document.getElementById('bkash-modal').style.display='none'" style="width: 100%; background: #f5f5f5; border: none; padding: 12px; cursor: pointer; color: #666; font-weight: bold;">CANCEL</button>
    </div>
</div>

<script>
    let selectedPrice = 0;
    let selectedPackName = "";
    let notifyInterval;
    let lastNotifyIndex = -1;

    function toggleTheme() {
        document.body.classList.toggle('light-mode');
        document.getElementById('theme-toggle').innerText = document.body.classList.contains('light-mode') ? "🌙" : "☀️";
    }

    const fakeOrders = [
        "ID 4521*** just bought Weekly!",
        "Success! user rafi*** got 40 Robux.",
        "UID 9982*** received Monthly!",
        "Order #8841 for user topup_pro*** completed!",
        "Success! ID 1025*** got 400 Robux.",
        "UID 7745*** just bought Weekly!"
    ];

    function startFake() {
        notifyInterval = setInterval(() => {
            const notify = document.getElementById('notify-box');
            notify.style.opacity = '0';
            setTimeout(() => {
                let newIndex;
                do {
                    newIndex = Math.floor(Math.random() * fakeOrders.length);
                } while (newIndex === lastNotifyIndex); // রিপিট হবে না
                
                lastNotifyIndex = newIndex;
                notify.innerText = fakeOrders[newIndex];
                notify.style.opacity = '1';
                notify.style.color = "var(--neon-yellow)";
            }, 500);
        }, 8000);
    }

    function verifyRealOrder() {
        if(document.getElementById('trx-input').value.length < 5) return alert("Invalid TrxID!");
        clearInterval(notifyInterval);
        const notify = document.getElementById('notify-box');
        notify.innerHTML = `<span style="color:#00cc66">✅ ORDER DONE! ${document.getElementById('uid-input').value} just purchased ${selectedPackName}.</span>`;
        alert("অর্ডার সফল!");
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
    function openPayment() { if(!selectedPrice) return alert("Select Pack!"); document.getElementById('bkash-modal').style.display = 'flex'; }
    function copyNum() { navigator.clipboard.writeText("01779772201"); alert("Copied!"); }

    startFake();
</script>

</body>
</html>
