function startCountdown() {
	var countdownTime = document.getElementById("countdown-time").value;
	var countdownDisplay = document.getElementById("countdown");
	var audio = document.getElementById("audio");

	var countdown = setInterval(function() {
		if (countdownTime <= 0) {
			clearInterval(countdown);
			countdownDisplay.innerHTML = "Time's up!";
			audio.play();
		} else {
			countdownDisplay.innerHTML = countdownTime;
			countdownTime--;
		}
	}, 1000);
}
