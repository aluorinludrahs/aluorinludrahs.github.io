<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Countdown Timer</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <div class="container">
      <h1>Countdown Timer</h1>
      <div class="countdown-box">
        <label for="countdown-number">Countdown from:</label>
        <input type="number" id="countdown-number" value="10" min="1">
      </div>
      <div class="countdown-box">
        <label for="interval">Interval (in seconds):</label>
        <input type="number" id="interval" value="1" min="1">
      </div>
      <div class="countdown-timer">
        <span id="minutes">00</span>:<span id="seconds">00</span>
      </div>
      <div class="button-container">
        <button id="start" class="button">Start</button>
        <button id="pause" class="button" disabled>Pause</button>
        <button id="reset" class="button">Reset</button>
      </div>
    </div>
    <script src="script.js"></script>
  </body>
</html>
