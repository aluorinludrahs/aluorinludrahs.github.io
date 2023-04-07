<!DOCTYPE html>
<html>
  <head>
    <title>Countdown Timer</title>
  </head>
  <body>
    <h1>Countdown Timer</h1>
    <label for="interval">Interval (in seconds):</label>
    <input type="number" id="interval" min="1" value="1">
    <br><br>
    <label for="start">Start number:</label>
    <input type="number" id="start" min="1" value="1">
    <br><br>
    <label for="end">End number:</label>
    <input type="number" id="end" min="1" value="10">
    <br><br>
    <button id="startButton">Start</button>
    <button id="pauseButton" disabled>Pause</button>
    <button id="playButton" disabled>Play</button>
    <button id="resetButton" disabled>Reset</button>
    <br><br>
    <div id="countdown"></div>
    <script>
      window.onload = function() {
        const startButton = document.getElementById('startButton');
        const pauseButton = document.getElementById('pauseButton');
        const playButton = document.getElementById('playButton');
        const resetButton = document.getElementById('resetButton');
        const countdownDisplay = document.getElementById('countdown');
        const intervalInput = document.getElementById('interval');
        const startInput = document.getElementById('start');
        const endInput = document.getElementById('end');

        let intervalId;
        let remainingTime;
        let intervalDuration = 1000;
        let currentNumber = startInput.value;
        let endNumber = endInput.value;
        
        function startCountdown() {
          intervalDuration = intervalInput.value * 1000;
          countdownDisplay.innerText = currentNumber;
          intervalId = setInterval(function() {
            currentNumber++;
            countdownDisplay.innerText = currentNumber;
            if (currentNumber >= endNumber) {
              clearInterval(intervalId);
              startButton.disabled = false;
              pauseButton.disabled = true;
              playButton.disabled = true;
              resetButton.disabled = false;
            }
          }, intervalDuration);
          startButton.disabled = true;
          pauseButton.disabled = false;
          playButton.disabled = true;
          resetButton.disabled = true;
        }

        function pauseCountdown() {
          clearInterval(intervalId);
          remainingTime = endNumber - currentNumber;
          startButton.disabled = true;
          pauseButton.disabled = true;
          playButton.disabled = false;
          resetButton.disabled = false;
        }

        function playCountdown() {
          intervalDuration = intervalInput.value * 1000;
          endNumber = currentNumber + remainingTime;
          intervalId = setInterval(function() {
            currentNumber++;
            countdownDisplay.innerText = currentNumber;
            if (currentNumber >= endNumber) {
              clearInterval(intervalId);
              startButton.disabled = false;
              pauseButton.disabled = true;
              playButton.disabled = true;
              resetButton.disabled = false;
            }
          }, intervalDuration);
          startButton.disabled = true;
          pauseButton.disabled = false;
          playButton.disabled = true;
          resetButton.disabled = true;
        }

       function resetCountdown() {
  clearInterval(intervalId);
  remainingTime = undefined;
  countdownDisplay.innerText = '';
  startInput.disabled = false;
  endInput.disabled = false;
  startButton.disabled = false;
  pauseButton.disabled = true;
  resetButton.disabled = true;
  countdownDisplay.innerText = startInput.value;
}
