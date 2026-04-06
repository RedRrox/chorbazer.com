<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CHOR BAZER | GAME TOP UP</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;800&family=Rajdhani:wght@500;700&display=swap" rel="stylesheet">
    <style>
        /* --- কালার এবং থিম সেটআপ (শুধুমাত্র ডার্ক থিম) --- */
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

        /* নোটিফিকেশন বক্স */
        #notify-box { 
            background: rgba(204, 255, 0, 0.05); 
            border: 1px dashed var(--neon-yellow); 
            padding: 12px; border-radius: 8px; margin-bottom: 20px; 
            text-align: center; font-weight: bold; color: var(--neon-yellow); font-size: 15px;
            transition: opacity 0.5s ease-in-out;
        }

        .box { background: var(--card-bg); border: 1px solid #222; padding: 20px; border-radius: 12px; margin-bottom: 20px; }
        h2 { font-size: 18px; margin-bottom: 15px; color: var(--neon-yellow); text-transform: uppercase; border-left: 4px solid var(--neon-yellow); padding-left: 10px; }

        input[type="text"] { 
            width: 100%; padding: 15px; background: var(--input-bg); 
            border: 1px solid #333; color: var(--neon-yellow); 
            border-radius: 8px; font-size: 18px; outline: none; text-align: center; font-weight: bold; 
        }

        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .item { background: #000; border: 1px solid #222; padding: 20px; border-radius: 10px; cursor: pointer; text-align: center; transition: 0.3s; }
        .item.active { border-color: var(--neon-yellow); background: rgba(204, 255, 0, 0.08); }
        .item .price { color: var(--neon-yellow); font-weight: bold; font-size: 22px; display: block; }

        /* স্পেশাল প্যাক */
        .premium-card { 
            grid-column: span 2; border: 2px solid var(--gold) !important; 
            background: linear-gradient(145deg, #1a1a1a, #000); cursor: not-allowed;
        }
        .stock-tag { background: #ff4444; color: #fff; font-size: 10px; padding: 2px 8px; border-radius: 4px; margin-top: 5px; display: inline-block; font-weight: 800; }

        .summary p { display: flex; justify-content: space-between; margin-bottom: 8px; color: #aaa; }
        .total { color: var(--neon-yellow); font-size: 24px; font-weight: bold; border-top: 1px solid #333; padding-top: 10px; margin-top: 10px; }
        
        .btn-buy { width: 100%; padding: 18px; background: var(--neon-yellow); color: #000; border: none; border-radius: 8px; font-weight: bold; font-size: 20px; cursor: pointer; margin-top: 10px; }

        /* --- অরিজিনাল বিকাশ মেনু স্টাইল --- */
        #bkash-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 9999; justify-content: center; align-items: center; }
        .bkash-content { background: #fff; width: 92%; max-width: 400px; border-radius: 15px; overflow: hidden; color: #000; box-shadow: 0 10px 30px rgba(0,0,0,0.5); }
        
        .bkash-header { 
            background: #fff; 
            height: 70px; 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            border-bottom: 1px solid #eee;
            padding: 10px;
        }
        /* বিকাশ লোগো ফিক্স: বাড়তি লেখা সরাতে object-fit ব্যবহার করা হয়েছে */
        .bkash-header img { 
            height: 100%; 
            max-width: 130px; 
            object-fit: contain; 
        }

        .bkash-body { background: var(--bkash-color); color: #fff; padding: 25px; text-align: left; }
        .instr { font-size: 14px; margin-bottom: 12px; border-bottom: 1px solid rgba(255,255,255,0.2); padding-bottom: 8px; }
        .instr b { color: var(--neon-yellow); font-size: 16px; }
        
        .trx-input { 
            width: 100%; padding: 15px; margin: 15px 0; border-radius: 8px; border: none; 
            font-size: 20px; text-align: center; font-weight: bold; text-transform: uppercase; color: #000;
        }

        .copy-btn { background: #fff; color: #000; border: none; padding: 4px 10px; border-radius: 5px; font-size: 11px; cursor: pointer; margin-left: 10px; font-weight: bold; }
        .delivery-tag { background: #fff9c4; color: #d32f2f; padding: 10px; font-size: 12px; text-align: center; font-weight: bold; }
        .verify-btn { width: 92%; margin: 15px auto; display: block; padding: 16px; background: #d00000; color: #fff; border: none; font-weight: bold; cursor: pointer; font-size: 18px; border-radius: 10px; }
    </style>
</head>
<body>

<header>
    <div class="logo">CHOR BAZER</div>
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
        <div class="bkash-header">
            <img src="bikashlogo.png" alt="bkash">
        </div>
        <div class="bkash-body">
            <p style="text-align: center; font-weight: bold; margin-bottom: 15px;">ট্রানজেকশন আইডি দিন</p>
            <input type="text" class="trx-input" id="trx-input" placeholder="TrxID">
            <div class="instr">● নম্বরঃ <b>01779772201</b> <button class="copy-btn" onclick="copyNum()">COPY</button></div>
            <div class="instr">● টাকার পরিমাণঃ ৳ <b id="pay-amount">0</b></div>
            <div class="instr">● পেমেন্ট শেষে ট্রানজেকশন আইডি উপরে দিন।</div>
        </div>
        <div class="delivery-tag">⚠️ ডেলিভারি সময় ৩০-৪০ মিনিট।</div>
        <button class="verify-btn" onclick="verifyRealOrder()">VERIFY</button>
        <button onclick="document.getElementById('bkash-modal').style.display='none'" style="width: 100%; background: #f5f5f5; border: none; padding: 12px; cursor: pointer; color: #666; font-weight: bold;">CANCEL</button>
    </div>
</div>

<script>
    let selectedPrice = 0;
    let selectedPackName = "";
    let notifyInterval;
    let lastOrderIndex = -1;

    // ফেক অর্ডার হিস্ট্রি (রিপিট হবে না)
    const fakeData = [
        "ID 4521*** just bought Weekly!",
        "Success! user rafi*** got 40 Robux.",
        "UID 9982*** received Monthly!",
        "Order #8841 for user topup_pro*** completed!",
        "Success! ID 1025*** got 400 Robux.",
        "UID 7745*** just bought Weekly!"
    ];

    function startFakeHistory() {
        notifyInterval = setInterval(() => {
            const notify = document.getElementById('notify-box');
            notify.style.opacity = '0';
            setTimeout(() => {
                let nextIndex;
                do {
                    nextIndex = Math.floor(Math.random() * fakeData.length);
                } while (nextIndex === lastOrderIndex);
                
                lastOrderIndex = nextIndex;
                notify.innerText = fakeData[nextIndex];
                notify.style.opacity = '1';
                notify.style.color = "var(--neon-yellow)";
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
        
        alert("অর্ডার সফল! ৩০-৪০ মিনিটে ডেলিভারি পাবেন।");
        document.getElementById('bkash-modal').style.display = 'none';
        setTimeout(startFakeHistory, 15000);
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

    startFakeHistory();
</script>

</body>
</html>
