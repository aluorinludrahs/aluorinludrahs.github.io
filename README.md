<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <meta name="description" content="Customizable Countdown Timer for Your Website">
    <title>Simple Countdown Timer with JavaScript</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.6.0/css/bootstrap.min.css">
    <style>
      /* add custom CSS styles here */
    </style>
  </head>
  <body>
    <div class="container">
      <h1>Simple Countdown Timer</h1>
      <div class="form-group">
        <label for="interval">Interval (in seconds):</label>
        <input type="number" id="interval" class="form-control" min="1" value="1">
      </div>
      <div class="form-group">
        <label for="start">Start number:</label>
        <input type="number" id="start" class="form-control" min="1" value="1">
      </div>
      <div class="form-group">
        <label for="end">End number:</label>
        <input type="number" id="end" class="form-control" min="1" value="10">
      </div>
      <button id="startButton" class="btn btn-primary">Start</button>
      <button id="pauseButton" class="btn btn-secondary" disabled>Pause</button>
      <button id="resetButton" class="btn btn-secondary" disabled>Reset</button>
      <br><br>
      <div id="countdown"></div>
    </div>
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

        function startCountdown() {
          if (!validateInputs()) {
            return;
          }

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

        // Add error handling to ensure that user inputs valid values
        function validateInputs() {
          if (startInput.value >= endInput.value) {
            alert("Please enter a start number that is less than the end number.");
    return false;
  }
  if (intervalInput.value <= 0) {
    alert("Please enter a valid interval value.");
    return false;
  }
  if (startInput.value <= 0 || endInput.value <= 0) {
    alert("Please enter positive values for start and end numbers.");
    return false;
  }
  return true;
}

function startCountdown() {
  if (!validateInputs()) {
    return;
  }

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
