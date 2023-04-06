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
    <audio id="countdownSound" src="path/to/sound/file.mp3"></audio>
    <script>
      window.onload = function() {
        const startButton = document.getElementById('startButton');
        const pauseButton = document.getElementById('pauseButton');
        const resetButton = document.getElementById('resetButton');
        const countdownDisplay = document.getElementById('countdown');
        const intervalInput = document.getElementById('interval');
        const startInput = document.getElementById('start');
        const endInput = document.getElementById('end');
        const countdownSound = document.getElementById('countdownSound');

        let intervalId;
        let remainingTime;
        let intervalDuration = 1000;

        function startCountdown() {
          intervalDuration = intervalInput.value * 1000;
          let currentNumber = startInput.value;
          const endNumber = endInput.value;
          countdownDisplay.innerText = currentNumber;
          intervalId = setInterval(function() {
            currentNumber++;
            countdownDisplay.innerText = currentNumber;
            if (currentNumber >= endNumber) {
              clearInterval(intervalId);
              startButton.disabled = false;
              pauseButton.disabled = true;
              resetButton.disabled = false;
            } else if (currentNumber % 1 === 0) {
              countdownSound.currentTime = 0;
              countdownSound.play();
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
