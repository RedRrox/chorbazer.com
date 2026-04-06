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
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Rajdhani', sans-serif; }
        body { background: var(--dark-bg); color: var(--text-main); padding-bottom: 50px; }

        header { 
            background: #000; 
            padding: 30px; 
            text-align: center; 
            border-bottom: 2px solid var(--neon-yellow); 
            box-shadow: 0 0 20px rgba(204, 255, 0, 0.2);
        }
        .logo { font-family: 'Orbitron', sans-serif; font-size: 35px; color: var(--neon-yellow); letter-spacing: 5px; }

        .container { max-width: 600px; margin: 20px auto; padding: 15px; }

        #notify-box { 
            background: rgba(204, 255, 0, 0.05); 
            border: 1px dashed var(--neon-yellow); 
            padding: 12px; border-radius: 8px; margin-bottom: 20px; 
            text-align: center; font-weight: bold; color: var(--neon-yellow); font-size: 15px;
        }

        .box { background: var(--card-bg); border: 1px solid #222; padding: 20px; border-radius: 12px; margin-bottom: 20px; position: relative; }
        h2 { font-size: 18px; margin-bottom: 15px; color: var(--neon-yellow); text-transform: uppercase; border-left: 4px solid var(--neon-yellow); padding-left: 10px; }

        input[type="text"] { 
            width: 100%; padding: 15px; background: var(--input-bg); 
            border: 1px solid #333; color: var(--neon-yellow); 
            border-radius: 8px; font-size: 18px; outline: none; text-align: center; font-weight: bold; 
        }

        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .item { background: #000; border: 1px solid #222; padding: 20px; border-radius: 10px; cursor: pointer; text-align: center; position: relative; overflow: hidden; }
        .item.active { border-color: var(--neon-yellow); background: rgba(204, 255, 0, 0.08); }
        .item .price { color: var(--neon-yellow); font-weight: bold; font-size: 22px; display: block; }

        /* --- Special Pack with Limited Badge --- */
        .premium-card { 
            grid-column: span 2; border: 2px solid var(--gold) !important; 
            background: linear-gradient(145deg, #1a1a1a, #000); cursor: not-allowed;
        }
        .premium-badge {
            position: absolute; top: 0; left: 0; background: var(--gold);
            color: #000; font-size: 10px; font-weight: 800; padding: 2px 10px;
            border-radius: 0 0 10px 0; box-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }
        .stock-tag { background: #ff4444; color: #fff; font-size: 10px; padding: 2px 8px; border-radius: 4px; margin-top: 5px; display: inline-block; }

        .summary p { display: flex; justify-content: space-between; margin-bottom: 8px; color: #aaa; }
        .total { color: var(--neon-yellow); font-size: 24px; font-weight: bold; border-top: 1px solid #333; padding-top: 10px; margin-top: 10px; }
        .btn-buy { width: 100%; padding: 18px; background: var(--neon-yellow); color: #000; border: none; border-radius: 8px; font-weight: bold; font-size: 20px; cursor: pointer; margin-top: 10px; }

        /* --- bKash Modal with Send Money Text --- */
        #bkash-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 9999; justify-content: center; align-items: center; }
        .bkash-content { background: #fff; width: 92%; max-width: 400px; border-radius: 15px; overflow: hidden; color: #000; }
        .bkash-header { background: #fff; height: 65px; display: flex; justify-content: center; align-items: center; border-bottom: 1px solid #eee; }
        .bkash-header img { height: 45px; width: auto; object-fit: contain; }

        .bkash-body { background: var(--bkash-color); color: #fff; padding: 20px; }
        .send-money-alert { text-align: center; font-weight: 800; font-size: 18px; margin-bottom: 10px; background: #fff; color: var(--bkash-color); padding: 5px; border-radius: 5px; }
        .trx-input { width: 100%; padding: 15px; margin: 10px 0; border-radius: 8px; border: none; font-size: 18px; text-align: center; font-weight: bold; }
        .instr { font-size: 14px; margin-bottom: 10px; border-bottom: 1px solid rgba(255,255,255,0.2); padding-bottom: 8px; }
        .instr b { color: var(--neon-yellow); font-size: 16px; }
        .copy-btn { background: #fff; color: #000; border: none; padding: 3px 8px; border-radius: 4px; font-size: 10px; cursor: pointer; margin-left: 10px; font-weight: bold; }
        .verify-btn { width: 90%; margin: 15px auto; display: block; padding: 16px; background: #d00000; color: #fff; border: none; font-weight: bold; cursor: pointer; border-radius: 10px; }
    </style>
</head>
<body>

<header><div class="logo">CHOR BAZER</div></header>

<div class="container">
    <div id="notify-box">🚀 Loading Market...</div>

    <div class="box">
        <h2>1. Player UID / Roblox Username</h2>
        <input type="text" id="uid-input" placeholder="Enter UID or Username" oninput="updateID()">
    </div>

    <div class="box">
        <h2>2. Select Pack</h2>
        <div class="grid">
            <div class="item premium-card">
                <div class="premium-badge">LIMITED TIME</div>
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
            <div class="send-money-alert">Send Money korte hobe</div>
            <p style="text-align: center; font-size: 13px; margin-bottom: 10px;">TrxID niche boshan</p>
            <input type="text" class="trx-input" id="trx-input" placeholder="Transaction ID">
            <div class="instr">● Number: <b>01779772201</b> <button class="copy-btn" onclick="copyNum()">COPY</button></div>
            <div class="instr">● Amount: ৳ <b id="pay-amount">0</b></div>
        </div>
        <button class="verify-btn" onclick="verifyRealOrder()">VERIFY</button>
        <button onclick="document.getElementById('bkash-modal').style.display='none'" style="width: 100%; background: #f5f5f5; border: none; padding: 12px; cursor: pointer; color: #666; font-weight: bold;">CANCEL</button>
    </div>
</div>

<script>
    let selectedPrice = 0;
    let selectedPackName = "";
    let notifyInterval;
    let lastIndex = -1;

    const fakeMsg = ["ID 4521***", "user rafi***", "UID 9982***", "user topup_pro***", "ID 1025***"];
    function startFake() {
        notifyInterval = setInterval(() => {
            const notify = document.getElementById('notify-box');
            notify.style.opacity = '0';
            setTimeout(() => {
                let idx; do { idx = Math.floor(Math.random() * fakeMsg.length); } while (idx === lastIndex);
                lastIndex = idx;
                notify.innerText = `${fakeMsg[idx]} just bought ${Math.random() > 0.5 ? 'Weekly' : '40 Robux'}!`;
                notify.style.opacity = '1';
            }, 500);
        }, 10000);
    }

    function verifyRealOrder() {
        if(document.getElementById('trx-input').value.length < 5) return alert("TrxID bhul!");
        clearInterval(notifyInterval);
        document.getElementById('notify-box').innerHTML = `<span style="color:#00ff88">✅ ORDER DONE! ${document.getElementById('uid-input').value} just purchased ${selectedPackName}.</span>`;
        alert("Order Successful! Delivery 30-40 mins.");
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
    function openPayment() { if(!selectedPrice) return alert("Pack select korun!"); document.getElementById('bkash-modal').style.display = 'flex'; }
    function copyNum() { navigator.clipboard.writeText("01779772201"); alert("Copied!"); }

    startFake();
</script>

</body>
</html>
