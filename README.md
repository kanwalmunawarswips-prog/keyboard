<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Fun Typing Game for Kids</title>
<style>
body {
  font-family: 'Comic Sans MS', cursive;
  text-align: center;
  background: linear-gradient(to right, #ffecd2, #fcb69f);
}
h1 { color: #ff4d6d; }
#gameBox {
  background: white;
  padding: 20px;
  border-radius: 20px;
  width: 70%;
  margin: auto;
  box-shadow: 0 0 15px rgba(0,0,0,0.2);
}
#sentence {
  font-size: 26px;
  margin: 20px;
  color: #333;
}
#inputBox {
  font-size: 22px;
  padding: 12px;
  width: 70%;
  border-radius: 10px;
  border: 2px solid #ff9a9e;
}
button {
  padding: 10px 20px;
  font-size: 18px;
  margin-top: 15px;
  border: none;
  border-radius: 10px;
  background: #ff758c;
  color: white;
  cursor: pointer;
}
.correct { color: green; font-size: 20px; }
.incorrect { color: red; font-size: 20px; }
#score, #timer {
  font-size: 20px;
  margin: 10px;
  color: #444;
}
</style>
</head>
<body>

<h1>🎮 Fun Typing Game</h1>
<div id="gameBox">
  <div id="score">Score: 0</div>
  <div id="timer">Time: 90s</div>
  <p id="sentence"></p>
  <input type="text" id="inputBox" placeholder="Type here..." />
  <br>
  <button onclick="nextSentence()">Next</button>
  <p id="result"></p>
</div>

<script>
const sentences = [
  "I like apples.",
  "The sun is hot.",
  "My cat is cute.",
  "We play games.",
  "This is my book.",
  "Birds can fly.",
  "I have a red ball.",
  "The sky is blue.",
  "I love my mom.",
  "We go to school."
];

let currentSentence = "";
let score = 0;
let timeLeft = 90;
let timer;

function startTimer() {
  timer = setInterval(() => {
    timeLeft--;
    document.getElementById("timer").innerText = "Time: " + timeLeft + "s";

    if (timeLeft <= 0) {
      clearInterval(timer);
      document.getElementById("result").innerHTML = "<span class='incorrect'>⏰ Time's up!</span>";
      document.getElementById("inputBox").disabled = true;
    }
  }, 1000);
}

function nextSentence() {
  currentSentence = sentences[Math.floor(Math.random() * sentences.length)];
  document.getElementById("sentence").innerText = currentSentence;
  document.getElementById("inputBox").value = "";
  document.getElementById("result").innerText = "";
}

const inputBox = document.getElementById("inputBox");
inputBox.addEventListener("input", function() {
  if (inputBox.value === currentSentence) {
    score++;
    document.getElementById("score").innerText = "Score: " + score;
    document.getElementById("result").innerHTML = "<span class='correct'>✔ Great Job!</span>";
    nextSentence();
  }
});

// Start game
nextSentence();
startTimer();
</script>

</body>
</html>
