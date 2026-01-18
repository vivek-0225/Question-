<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WARNING: ROASTING IN PROGRESS ⚠️</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Courier+Prime:wght@700&family=Permanent+Marker&display=swap');
        
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            background: #000; 
            color: #0f0; 
            font-family: 'Courier Prime', monospace; 
            overflow: hidden;
            display: flex; justify-content: center; align-items: center; height: 100vh;
        }

        #glitch-bg {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: repeating-linear-gradient(0deg, rgba(0,255,0,0.03) 0px, rgba(0,255,0,0.03) 1px, transparent 1px, transparent 2px);
            pointer-events: none; z-index: -1;
        }

        .card {
            background: rgba(20, 20, 20, 0.9);
            border: 2px solid #0f0;
            padding: 30px;
            width: 90%; max-width: 450px;
            text-align: center;
            box-shadow: 0 0 20px #0f0;
        }

        h1 { font-family: 'Permanent Marker', cursive; color: #ff003c; margin-bottom: 20px; font-size: 1.5rem; text-transform: uppercase; }
        
        .question { font-size: 1.2rem; margin-bottom: 25px; color: #fff; line-height: 1.4; }

        .btn-container { display: flex; flex-direction: column; gap: 15px; }

        button {
            background: transparent;
            border: 1px solid #0f0;
            color: #0f0;
            padding: 12px;
            font-size: 1rem;
            cursor: pointer;
            transition: 0.2s;
            font-family: 'Courier Prime', monospace;
        }

        button:hover { background: #0f0; color: #000; box-shadow: 0 0 15px #0f0; }

        #final-msg { display: none; color: #ff003c; font-size: 1.5rem; animation: shake 0.5s infinite; }

        @keyframes shake {
            0% { transform: translate(1px, 1px) rotate(0deg); }
            20% { transform: translate(-3px, 0px) rotate(1deg); }
            40% { transform: translate(1px, -1px) rotate(1deg); }
            60% { transform: translate(-1px, 1px) rotate(0deg); }
            80% { transform: translate(-1px, -1px) rotate(1deg); }
            100% { transform: translate(1px, -2px) rotate(-1deg); }
        }
    </style>
</head>
<body>

<div id="glitch-bg"></div>

<div class="card" id="game-card">
    <div id="intro">
        <h1>⚠️ SYSTEM CRITICAL ⚠️</h1>
        <p style="margin-bottom: 20px;">Tumhare dimaag ka scan chal raha hai... Result dekhne ki himmat hai?</p>
        <button onclick="startGame()">YES, I'M READY (Darna mana hai)</button>
    </div>

    <div id="quiz" style="display: none;">
        <p id="q-num" style="color: #888; font-size: 0.8rem; margin-bottom: 10px;"></p>
        <p class="question" id="q-text"></p>
        <div class="btn-container" id="options"></div>
    </div>

    <div id="final-msg">
        <h1>ROAST FINISHED! 🔥</h1>
        <p id="roast-summary"></p>
        <button onclick="location.reload()" style="margin-top:20px;">CHAL PHIR SE BEIZZATI KARA</button>
    </div>
</div>

<script>
    const questions = [
        { q: "Tumhe kya lagta hai, tumhare andar dimaag hai?", a: ["Nahi hai", "Galti se bhi nahi hai"] },
        { q: "Subah uth kar sabse pehle kya karti ho?", a: ["Aina todti hoon", "Duniya ko darati hoon"] },
        { q: "Agar tum alien hoti toh kya karti?", a: ["Wapas bhaag jati", "Aliens ko bhi pagal kar deti"] },
        { q: "Tumhari sabse badi superpower kya hai?", a: ["Bin baat ke rona", "Faltu ka gyan dena"] },
        { q: "Log tumhe dekh kar kya sochte hain?", a: ["Bhagwan bachaye!", "Ye zinda kaise hai?"] },
        { q: "Tumhare makeup ka asli maqsad kya hai?", a: ["Asliyat chhupana", "Bachon ko darana"] },
        { q: "Agar tumhe 'Zero' award mile toh?", a: ["Mera haq hai", "Main iske bhi layak nahi"] },
        { q: "Tumhari baaton ka logic kahan hota hai?", a: ["Dustbin mein", "Logic kya hota hai?"] },
        { q: "Tumhara best friend tumhare baare mein kya sochta hai?", a: ["Ye thodi pagal hai", "Ye poori pagal hai"] },
        { q: "Final Question: Kya tum sudharne ka irada rakhti ho?", a: ["Bilkul nahi", "Umeed mat rakho"] }
    ];

    let currentQ = 0;

    function startGame() {
        document.getElementById('intro').style.display = 'none';
        document.getElementById('quiz').style.display = 'block';
        showQuestion();
    }

    function showQuestion() {
        if(currentQ < questions.length) {
            document.getElementById('q-num').innerText = `ROAST ${currentQ + 1} / 10`;
            document.getElementById('q-text').innerText = questions[currentQ].q;
            const optionsDiv = document.getElementById('options');
            optionsDiv.innerHTML = "";
            questions[currentQ].a.forEach(opt => {
                const btn = document.createElement('button');
                btn.innerText = opt;
                btn.onclick = () => { currentQ++; showQuestion(); };
                optionsDiv.appendChild(btn);
            });
        } else {
            showFinal();
        }
    }

    function showFinal() {
        document.getElementById('quiz').style.display = 'none';
        document.getElementById('final-msg').style.display = 'block';
        document.getElementById('roast-summary').innerText = "Report: 100% Namuna Detected. Tumhare liye koi ilaaj nahi bana! 😂";
    }
</script>

</body>
</html>
