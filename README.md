<!DOCTYPE html>
<html>
  <head>
    <title>Countdown Timer</title>
    <link rel="stylesheet" type="text/css" href="style.css">
  </head>
  <body>
    <div class="container">
      <h1>Countdown Timer</h1>
      <div class="countdown">
        <div class="timer">
          <span id="minutes"></span>
          <span>:</span>
          <span id="seconds"></span>
        </div>
        <div class="controls">
          <label for="interval">Interval:</label>
          <input type="number" id="interval" value="1" min="1">
          <button id="start">Start</button>
          <button id="pause">Pause</button>
          <button id="reset">Reset</button>
        </div>
      </div>
    </div>
    <script src="script.js"></script>
  </body>
</html>
