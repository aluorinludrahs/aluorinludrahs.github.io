<!DOCTYPE html>
<html>
<head>
	<title>Counting Numbers</title>
	<script type="text/javascript">
		var count = 0;
		var delay = 1000;
		var timer = null;

		function startCount() {
			timer = setInterval(function() {
				document.getElementById("count").innerHTML = count++;
			}, delay);
		}

		function pauseCount() {
			clearInterval(timer);
			timer = null;
		}

		function resetCount() {
			count = 0;
			document.getElementById("count").innerHTML = count;
			pauseCount();
		}

		function changeDelay() {
			delay = document.getElementById("delay").value;
			pauseCount();
			startCount();
		}
	</script>
</head>
<body>
	<h1>Counting Numbers</h1>
	<p>Number: <span id="count">0</span></p>
	<label for="delay">Delay (in milliseconds): </label>
	<input type="number" id="delay" value="1000">
	<button onclick="startCount()">Start</button>
	<button onclick="pauseCount()">Pause</button>
	<button onclick="resetCount()">Reset</button>
	<div style="margin-top: 10px;">
		<label for="delay-control">Time Delay Control (in milliseconds): </label>
		<input type="range" id="delay-control" min="100" max="5000" step="100" value="1000" onchange="changeDelay()">
	</div>
</body>
</html>
