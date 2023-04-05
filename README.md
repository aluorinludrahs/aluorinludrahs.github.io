<!DOCTYPE html>
<html>
  <head>
    <title>Countdown Timer</title>
    <style>
      body {
        background-color: #f2f2f2;
        font-family: Arial, sans-serif;
      }

      h1 {
        text-align: center;
        color: #333;
      }

      form {
        text-align: center;
      }

      label {
        font-weight: bold;
        color: #333;
      }

      input[type=number] {
        padding: 8px;
        border-radius: 4px;
        border: none;
        background-color: #ddd;
      }

      button {
        background-color: #333;
        color: #fff;
        padding: 10px 20px;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        margin-right: 10px;
      }

      button:hover {
        background-color: #444;
      }

      button:disabled {
        background-color: #bbb;
        color: #333;
        cursor: default;
      }

      #countdown {
        font-size: 50px;
        text-align: center;
        margin-top: 30px;
        color: #333;
      }

      #digital-watch {
        font-size: 25px;
        text-align: center;
        margin-top: 30px;
        color: #333;
      }
    </style>
  </head>
  <body>
    <h1>Countdown Timer</h1>
    <form>
      <label for="interval">Interval (in seconds):</label>
      <input type="number" id="interval" min="1" value="1">
      <br><br>
      <label for="start">Start number:</label>
      <input type="number" id="start" min="1" value="1">
      <br><br>
      <label for="end">End number:</label>
      <input type="number" id="end" min="1" value="10">
      <br><br>
      <label for="digits">Number of digits:</label>
      <input type="number" id="digits" min="1" value="2">
      <br><br>
      <button id="startButton">Start</button>
      <button id="pauseButton" disabled>Pause</button>
      <button id="resetButton" disabled>Reset</button>
    </form>
    <div id="countdown"></div>
    <div id="digital-watch"></div>
    <script>
      window.onload = function() {
        const startButton = document.getElementById('startButton');
        const pauseButton = document.getElementById('pauseButton');
        const resetButton = document.getElementById('resetButton');
        const countdownDisplay = document.getElementById('countdown');
        const watchDisplay = document.getElementById('digital-watch');
        const intervalInput = document.getElementById('interval');
        const startInput = document.getElementById('start');
        const endInput = document.getElementById('end');
        const digitsInput = document.getElementById('digits');

        let intervalId;
        let remainingTime;
        let intervalDuration = 1000;

        function startCountdown() {
          intervalDuration = intervalInput.value * 1000;
          let currentNumber = startInput.value;
          const endNumber = endInput.value;
          countdownDisplay.innerText = padNumber(currentNumber, digitsInput.value);
          watchDisplay.innerText = getCurrentTime();
          intervalId = setInterval(function() {
            currentNumber++;
            countdownDisplay.innerText = padNumber(currentNumber, digitsInput.value);
           
function startCountdown() {
  intervalDuration = intervalInput.value * 1000;
  let currentNumber = startInput.value;
  const endNumber = endInput.value;
  countdownDisplay.innerText = padNumber(currentNumber, digitsInput.value);
  watchDisplay.innerText = getCurrentTime();
  intervalId = setInterval(function() {
    currentNumber++;
    countdownDisplay.innerText = padNumber(currentNumber, digitsInput.value);
    watchDisplay.innerText = getCurrentTime();
    if (currentNumber >= endNumber) {
      clearInterval(intervalId);
      startButton.disabled = false;
      pauseButton.disabled = true;
      resetButton.disabled = false;
    }
  }, intervalDuration);
  startButton.disabled = true;
  pauseButton.disabled = false;
  resetButton.disabled = true;
}

function pauseCountdown() {
  clearInterval(intervalId);
  startButton.disabled = false;
  pauseButton.disabled = true;
  resetButton.disabled = false;
}

function resetCountdown() {
  clearInterval(intervalId);
  remainingTime = undefined;
  countdownDisplay.innerText = '';
  watchDisplay.innerText = getCurrentTime();
  startButton.disabled = false;
  pauseButton.disabled = true;
  resetButton.disabled = true;
}

function padNumber(number, digits) {
  return number.toString().padStart(digits, '0');
}

function getCurrentTime() {
  const now = new Date();
  const hours = padNumber(now.getHours(), 2);
  const minutes = padNumber(now.getMinutes(), 2);
  const seconds = padNumber(now.getSeconds(), 2);
  return `${hours}:${minutes}:${seconds}`;
}

startButton.addEventListener('click', startCountdown);
pauseButton.addEventListener('click', pauseCountdown);
resetButton.addEventListener('click', resetCountdown);
}
