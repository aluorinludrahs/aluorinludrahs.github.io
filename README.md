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
    <button id="resetButton" disabled>Reset</button>
    <br><br>
    <div id="countdown"></div>
    <script>
      window.onload = function() {
        const startButton = document.getElementById('startButton');
        const pauseButton = document.getElementById('pauseButton');
        const resetButton = document.getElementById('resetButton');
        const countdownDisplay = document.getElementById('countdown');
        const intervalInput = document.getElementById('interval');
        const startInput = document.getElementById('start');
        const endInput = document.getElementById('end');

        let intervalId;
        let remainingTime;
        let intervalDuration = 1000;

        // Define sound files for each number
        const soundFiles = {
          1: new Audio('C:\Users\shard\Downloads\FOR GITHUB\1.mp3'),
          2: new Audio('C:\Users\shard\Downloads\FOR GITHUB\2.mp3'),
          3: new Audio('C:\Users\shard\Downloads\FOR GITHUB\3.mp3'),
          // Add more sound files for each number
        };

        function startCountdown() {
          intervalDuration = intervalInput.value * 1000;
          let currentNumber = startInput.value;
          const endNumber = endInput.value;
          countdownDisplay.innerText = currentNumber;
          intervalId = setInterval(function() {
            currentNumber++;
            countdownDisplay.innerText = currentNumber;
            // Play sound file for current number
            soundFiles[currentNumber].play();
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
          startButton.disabled = false;
          pauseButton.disabled = true;
          resetButton.disabled = true;
        }

        startButton.addEventListener('click', startCountdown);
        pauseButton.addEventListener('click', pauseCountdown);
        resetButton.addEventListener('click', resetCountdown);
      }
    </script>
  </body>
</html>
