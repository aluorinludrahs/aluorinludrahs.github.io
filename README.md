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
	</script>
</head>
<body>
	<h1>Counting Numbers</h1>
	<p>Number: <span id="count">0</span></p>
	<button onclick="startCount()">Start</button>
	<button onclick="pauseCount()">Pause</button>
	<button onclick="resetCount()">Reset</button>
</body>
</html>
