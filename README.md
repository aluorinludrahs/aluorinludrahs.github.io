<!DOCTYPE html>
<html>
<head>
	<title>Countdown Timer</title>
</head>
<body>
	<h1>Countdown Timer</h1>
	<div>
		<label for="countdown-interval">Countdown Interval:</label>
		<input type="number" id="countdown-interval" value="5"> seconds
	</div>
	<div>
		<button onclick="startCountdown()">Start Countdown</button>
		<button onclick="stopCountdown()">Stop Countdown</button>
	</div>
	<div id="countdown-timer"></div>
	<audio id="alert-sound">
		<source src="alert.mp3" type="audio/mpeg">
		Your browser does not support the audio element.
	</audio>
	<script>
		var countdownInterval;
		var countdownTime;
		var alertSound = document.getElementById("alert-sound");

		function startCountdown() {
			var intervalInput = document.getElementById("countdown-interval");
			countdownTime = intervalInput.value;

			countdownInterval = setInterval(function() {
				countdownTime--;
				updateTimer();

				if (countdownTime == 0) {
					playAlertSound();
					clearInterval(countdownInterval);
				}
			}, 1000);
		}

		function stopCountdown() {
			clearInterval(countdownInterval);
			countdownTime = 0;
			updateTimer();
		}

		function updateTimer() {
			var countdownTimer = document.getElementById("countdown-timer");
			countdownTimer.innerHTML = countdownTime + " seconds";
		}

		function playAlertSound() {
			alertSound.play();
		}
	</script>
</body>
</html>
