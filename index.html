<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Drag & Drop Place Value</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            text-align: center;
            background-color: #f7fafc;
            color: #2d3748;
            margin: 0;
            padding: 15px;
            user-select: none;
        }
        .container {
            max-width: 800px;
            margin: auto;
            background: white;
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.08);
        }
        h1 { color: #1a365d; margin: 0 0 5px 0; font-size: 1.8rem; }
        .score-board {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 15px;
            font-weight: bold;
        }
        .streak { color: #dd6b20; }
        .high-score { color: #3182ce; }
        .target-box {
            font-size: 2.5rem;
            font-weight: 800;
            color: #2b6cb0;
            background: #ebf8ff;
            padding: 10px 25px;
            border-radius: 12px;
            display: inline-block;
            margin-bottom: 15px;
            border: 2px solid #bee3f8;
        }
        .instructions {
            color: #718096;
            margin: 0 0 15px 0;
            font-size: 0.95rem;
        }

        /* Supply Dock styling */
        .supply-dock {
            background: #edf2f7;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 20px;
            border: 2px solid #e2e8f0;
        }
        .dock-title {
            font-weight: bold;
            margin-bottom: 10px;
            color: #4a5568;
            font-size: 0.9rem;
            text-transform: uppercase;
        }
        .dock-items {
            display: flex;
            justify-content: space-around;
            align-items: center;
        }
        .dock-item-wrapper {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
            width: 30%;
        }

        /* Drop Zones Grid */
        .grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin-bottom: 20px;
        }
        .column {
            padding: 15px;
            border-radius: 12px;
            border: 2px dashed #cbd5e0;
            min-height: 220px;
            transition: background-color 0.2s;
        }
        .column.drag-over {
            background-color: rgba(66, 153, 225, 0.15) !important;
            border-color: #4299e1 !important;
        }
        .hundreds { background-color: #fefcbf; border-color: #ecc94b; }
        .tens { background-color: #feebc8; border-color: #ed8936; }
        .ones { background-color: #c6f6d5; border-color: #48bb78; }
        
        .label { font-weight: bold; font-size: 1.1rem; margin-bottom: 5px; color: #2d3748; }
        .count-badge {
            background: rgba(0,0,0,0.06);
            padding: 2px 8px;
            border-radius: 20px;
            font-size: 0.9rem;
            margin-bottom: 10px;
            display: inline-block;
        }
        
        /* Interactive Block Containers inside columns */
        .drop-zone-content {
            display: flex;
            flex-wrap: wrap;
            gap: 6px;
            justify-content: center;
            align-content: flex-start;
            min-height: 150px;
        }

        /* Base-10 Block Graphics */
        .flat {
            width: 45px;
            height: 45px;
            background: #ecc94b;
            border: 1px solid #d69e2e;
            box-sizing: border-box;
            cursor: grab;
            background-image: linear-gradient(to right, transparent 9%, rgba(0,0,0,0.12) 9%, rgba(0,0,0,0.12) 10%, transparent 10%), linear-gradient(to bottom, transparent 9%, rgba(0,0,0,0.12) 9%, rgba(0,0,0,0.12) 10%, transparent 10%);
            background-size: 4.5px 4.5px;
            border-radius: 2px;
        }
        .rod {
            width: 10px;
            height: 50px;
            background: #ed8936;
            border: 1px solid #dd6b20;
            box-sizing: border-box;
            cursor: grab;
            background-image: linear-gradient(to bottom, transparent 9%, rgba(0,0,0,0.12) 9%, rgba(0,0,0,0.12) 10%, transparent 10%);
            background-size: 10px 5px;
            border-radius: 1px;
        }
        .unit {
            width: 10px;
            height: 10px;
            background: #48bb78;
            border: 1px solid #38a169;
            cursor: grab;
            border-radius: 1px;
        }
        .flat:active, .rod:active, .unit:active { cursor: grabbing; }

        /* Equation Box */
        .equation-box {
            font-size: 1.3rem;
            font-weight: bold;
            background: #f7fafc;
            padding: 12px;
            border-radius: 12px;
            border: 2px solid #e2e8f0;
            margin-bottom: 20px;
            color: #4a5568;
        }
        .equation-val { color: #2b6cb0; }

        /* Control Buttons */
        .btn-container {
            display: flex;
            justify-content: center;
            gap: 10px;
        }
        button {
            color: white;
            border: none;
            padding: 12px 30px;
            font-size: 1.1rem;
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
        }
        .btn-check { background-color: #4299e1; box-shadow: 0 4px 6px rgba(66, 153, 225, 0.2); }
        .btn-check:hover { background-color: #3182ce; }
        .btn-clear { background-color: #a0aec0; }
        .btn-clear:hover { background-color: #718096; }
        
        .feedback {
            margin-top: 15px;
            font-size: 1.2rem;
            font-weight: bold;
            min-height: 30px;
        }
        .correct { color: #38a169; }
        .incorrect { color: #e53e3e; }
    </style>
</head>
<body>

<div class="container">
    <h1>Place Value Playground</h1>
    <p class="instructions">Drag blocks from the supply dock into the correct column targets!</p>
    
    <div class="score-board">
        <span class="streak">🔥 Streak: <span id="streakCount">0</span></span>
        <span class="high-score">🏆 Best: <span id="highScoreCount">0</span></span>
    </div>
    
    <div class="target-box" id="targetNumber">---</div>

    <!-- Infinite Supply Dock -->
    <div class="supply-dock">
        <div class="dock-title">📦 Block Supply Dock (Drag from here)</div>
        <div class="dock-items">
            <div class="dock-item-wrapper">
                <div class="flat" draggable="true" id="supplyFlat" ondragstart="drag(event, 'hundred')"></div>
                <small>Hundred Flat</small>
            </div>
            <div class="dock-item-wrapper">
                <div class="rod" draggable="true" id="supplyRod" ondragstart="drag(event, 'ten')"></div>
                <small>Ten Rod</small>
            </div>
            <div class="dock-item-wrapper">
                <div class="unit" draggable="true" id="supplyUnit" ondragstart="drag(event, 'one')"></div>
                <small>One Unit</small>
            </div>
        </div>
    </div>
    
    <!-- Workspace Drop Columns -->
    <div class="grid">
        <div class="column hundreds" ondragover="allowDrop(event)" ondragleave="dragLeave(event)" ondrop="drop(event, 'hundreds')">
            <div class="label">Hundreds</div>
            <div class="count-badge"><span id="countH">0</span> flats (= <span id="valH">0</span>)</div>
            <div class="drop-zone-content" id="zoneHundreds"></div>
        </div>
        <div class="column tens" ondragover="allowDrop(event)" ondragleave="dragLeave(event)" ondrop="drop(event, 'tens')">
            <div class="label">Tens</div>
            <div class="count-badge"><span id="countT">0</span> rods (= <span id="valT">0</span>)</div>
            <div class="drop-zone-content" id="zoneTens"></div>
        </div>
        <div class="column ones" ondragover="allowDrop(event)" ondragleave="dragLeave(event)" ondrop="drop(event, 'ones')">
            <div class="label">Ones</div>
            <div class="count-badge"><span id="countO">0</span> units (= <span id="valO">0</span>)</div>
            <div class="drop-zone-content" id="zoneOnes"></div>
        </div>
    </div>

    <!-- Live Equation Generator -->
    <div class="equation-box">
        Your Value: <span class="equation-val" id="eqH">0</span> + <span class="equation-val" id="eqT">0</span> + <span class="equation-val" id="eqO">0</span> = <span id="eqTotal">0</span>
    </div>

    <div class="btn-container">
        <button class="btn-clear" onclick="clearWorkspace()">Clear Board</button>
        <button class="btn-check" id="actionBtn" onclick="checkAnswer()">Check Answer</button>
    </div>
    
    <div class="feedback" id="feedback"></div>
</div>

<script>
    let currentNumber = 0;
    let targetH = 0, targetT = 0, targetO = 0;
    let currentH = 0, currentT = 0, currentO = 0;
    let streak = 0, highScore = 0;
    let isCorrectState = false;

    function generateNumber() {
        currentNumber = Math.floor(Math.random() * 900) + 100;
        targetH = Math.floor(currentNumber / 100);
        targetT = Math.floor((currentNumber % 100) / 10);
        targetO = currentNumber % 10;

        document.getElementById('targetNumber').innerText = currentNumber;
        clearWorkspace();
        
        // Reset check button state
        const btn = document.getElementById('actionBtn');
        btn.innerText = "Check Answer";
        btn.className = "btn-check";
        btn.setAttribute("onclick", "checkAnswer()");
        isCorrectState = false;
    }

    // Drag and Drop Logic Engines
    function drag(ev, blockType) {
        ev.dataTransfer.setData("text/plain", blockType);
    }

    function allowDrop(ev) {
        ev.preventDefault();
        ev.currentTarget.classList.add('drag-over');
    }

    function dragLeave(ev) {
        ev.currentTarget.classList.remove('drag-over');
    }

    function drop(ev, columnType) {
        ev.preventDefault();
        const column = ev.currentTarget;
        column.classList.remove('drag-over');
        
        if (isCorrectState) return; // Freeze if problem is solved
        
        const blockType = ev.dataTransfer.getData("text/plain");
        
        // Safety guard: Enforce correct column matching to assist young learners
        if (columnType === 'hundreds' && blockType !== 'hundred') return;
        if (columnType === 'tens' && blockType !== 'ten') return;
        if (columnType === 'ones' && blockType !== 'one') return;

        addBlockToColumn(columnType);
        clearFeedback();
    }

    function addBlockToColumn(columnType) {
        if (columnType === 'hundreds' && currentH < 9) {
            currentH++;
            document.getElementById('zoneHundreds').innerHTML += '<div class="flat" onclick="removeBlock(this, \'hundreds\')"></div>';
        } else if (columnType === 'tens' && currentT < 9) {
            currentT++;
            document.getElementById('zoneTens').innerHTML += '<div class="rod" onclick="removeBlock(this, \'tens\')"></div>';
        } else if (columnType === 'ones' && currentO < 9) {
            currentO++;
            document.getElementById('zoneOnes').innerHTML += '<div class="unit" onclick="removeBlock(this, \'ones\')"></div>';
        }
        calculateLiveValues();
    }

    // Click dropped block directly to discard it 
    function removeBlock(element, columnType) {
        if (isCorrectState) return;
        element.remove();
        if (columnType === 'hundreds') currentH--;
        if (columnType === 'tens') currentT--;
        if (columnType === 'ones') currentO--;
        calculateLiveValues();
        clearFeedback();
    }

    function calculateLiveValues() {
        // Quantities
        document.getElementById('countH').innerText = currentH;
        document.getElementById('countT').innerText = currentT;
        document.getElementById('countO').innerText = currentO;
        
        // Multiplied Values
        const valH = currentH * 100;
        const valT = currentT * 10;
        
        document.getElementById('valH').innerText = valH;
        document.getElementById('valT').innerText = valT;
        document.getElementById('valO').innerText = currentO;

        // Expanded Display Equation math
        document.getElementById('eqH').innerText = valH;
        document.getElementById('eqT').innerText = valT;
        document.getElementById('eqO').innerText = currentO;
        document.getElementById('eqTotal').innerText = valH + valT + currentO;
    }

    function clearWorkspace() {
        currentH = 0; currentT = 0; currentO = 0;
        document.getElementById('zoneHundreds').innerHTML = '';
        document.getElementById('zoneTens').innerHTML = '';
        document.getElementById('zoneOnes').innerHTML = '';
        calculateLiveValues();
        clearFeedback();
    }

    function checkAnswer() {
        const feedbackDiv = document.getElementById('feedback');

        if (currentH === targetH && currentT === targetT && currentO === targetO) {
            feedbackDiv.innerText = "🎉 Incredible! You built the number perfectly!";
            feedbackDiv.className = "feedback correct";
            
            streak++;
            if (streak > highScore) highScore = streak;
            updateScores();

            const btn = document.getElementById('actionBtn');
            btn.innerText = "Next Number 👉";
            btn.setAttribute("onclick", "generateNumber()");
            isCorrectState = true;
        } else {
            feedbackDiv.innerText = "❌ The blocks don't match the number target yet. Count carefully!";
            feedbackDiv.className = "feedback incorrect";
            streak = 0;
            updateScores();
        }
    }

    function clearFeedback() {
        if (!isCorrectState) document.getElementById('feedback').innerText = '';
    }

    function updateScores() {
        document.getElementById('streakCount').innerText = streak;
        document.getElementById('highScoreCount').innerText = highScore;
    }

    window.onload = generateNumber;
</script>

</body>
</html>
