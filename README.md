<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Place Value Playground</title>

<style>
body {
    font-family: 'Segoe UI', sans-serif;
    text-align: center;
    background-color: #f7fafc;
    margin: 0;
    padding: 15px;
}
.container {
    max-width: 800px;
    margin: auto;
    background: white;
    padding: 25px;
    border-radius: 20px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.08);
}
.target-box {
    font-size: 2.5rem;
    font-weight: bold;
    margin-bottom: 10px;
}
.grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
    margin: 20px 0;
}
.column {
    padding: 15px;
    border: 2px dashed #ccc;
    min-height: 200px;
}
.hundreds { background: #fefcbf; }
.tens { background: #feebc8; }
.ones { background: #c6f6d5; }
.flat, .rod, .unit {
    margin: 5px;
    cursor: grab;
}
.flat { width: 40px; height: 40px; background: gold; }
.rod { width: 10px; height: 50px; background: orange; }
.unit { width: 10px; height: 10px; background: green; }

button {
    padding: 10px 20px;
    margin: 5px;
    font-weight: bold;
    cursor: pointer;
}
.feedback {
    margin-top: 15px;
    font-weight: bold;
}
</style>
</head>

<body>

<div class="container">

<h2>Place Value Playground</h2>
<p id="modeIndicator"></p>
<p><strong>Problem <span id="problemNumber">1</span> of 10</strong></p>

<div class="target-box" id="targetNumber">---</div>

<!-- Supply -->
<div>
    <div class="flat" draggable="true" ondragstart="drag(event,'hundred')"></div>
    <div class="rod" draggable="true" ondragstart="drag(event,'ten')"></div>
    <div class="unit" draggable="true" ondragstart="drag(event,'one')"></div>
</div>

<!-- Columns -->
<div class="grid">
    <div class="column hundreds" ondragover="allowDrop(event)" ondrop="drop(event,'hundreds')"></div>
    <div class="column tens" ondragover="allowDrop(event)" ondrop="drop(event,'tens')"></div>
    <div class="column ones" ondragover="allowDrop(event)" ondrop="drop(event,'ones')"></div>
</div>

<button onclick="checkAnswer()">Check</button>
<button onclick="clearWorkspace()">Clear</button>

<br>

<button id="nextSlideBtn" style="display:none;" onclick="goToNextSlide()">
👉 Return to Nearpod
</button>

<div class="feedback" id="feedback"></div>

</div>

<script>

let currentNumber;
let targetH, targetT, targetO;
let currentH=0, currentT=0, currentO=0;

let problemCount = 0;
const maxProblems = 10;

// GENERATE NUMBER
function generateNumber(){

    if(problemCount >= maxProblems){
        document.getElementById('targetNumber').innerText = "Done!";
        document.getElementById('feedback').innerText =
        "🎉 Great work! Click below to return to Nearpod.";
        document.getElementById('nextSlideBtn').style.display = "inline-block";
        return;
    }

    problemCount++;
    document.getElementById('problemNumber').innerText = problemCount;

    currentNumber = Math.floor(Math.random()*900)+100;

    targetH = Math.floor(currentNumber/100);
    targetT = Math.floor((currentNumber%100)/10);
    targetO = currentNumber%10;

    document.getElementById('targetNumber').innerText = currentNumber;

    clearWorkspace();
    updateMode();
}

// MODE SWITCH
function updateMode(){
    let text = problemCount <=5 ?
    "Guided Mode: Place blocks in the correct column" :
    "Challenge Mode: Blocks can go anywhere!";

    document.getElementById('modeIndicator').innerText = text;
}

// DRAG
function drag(ev,type){
    ev.dataTransfer.setData("text",type);
}

function allowDrop(ev){
    ev.preventDefault();
}

// DROP
function drop(ev,column){
    ev.preventDefault();

    let type = ev.dataTransfer.getData("text");
    let guided = problemCount <=5;

    if(guided){
        if(column==="hundreds" && type!=="hundred") return;
        if(column==="tens" && type!=="ten") return;
        if(column==="ones" && type!=="one") return;
    }

    addBlock(column,type);
}

// ADD BLOCK
function addBlock(column,type){

    if(column==="hundreds"){
        currentH++;
        evAppend("hundreds","flat");
    }
    if(column==="tens"){
        currentT++;
        evAppend("tens","rod");
    }
    if(column==="ones"){
        currentO++;
        evAppend("ones","unit");
    }
}

// APPEND ELEMENT
function evAppend(col,className){
    let div = document.createElement("div");
    div.className = className;
    div.onclick = function(){ this.remove(); };
    document.querySelector("."+col).appendChild(div);
}

// CLEAR
function clearWorkspace(){
    currentH=0; currentT=0; currentO=0;
    document.querySelectorAll(".column").forEach(c=>c.innerHTML="");
}

// CHECK
function checkAnswer(){

    if(currentH===targetH && currentT===targetT && currentO===targetO){
        document.getElementById('feedback').innerText="✅ Correct!";
        setTimeout(generateNumber,1000);
    } else {
        document.getElementById('feedback').innerText="❌ Try again!";
    }
}

// RETURN TO NEARPOD (BEST METHOD)
function goToNextSlide(){
    alert("Close this tab or press the back button to return to Nearpod, then click NEXT.");
}

window.onload = generateNumber;

</script>

</body>
</html>
