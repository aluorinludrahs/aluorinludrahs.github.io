<!DOCTYPE html>
<html>
<head>
  <title>Bike Race Game</title>
  <style>
    /* CSS styles for the game */
    #game-container {
      width: 800px;
      height: 400px;
      border: 1px solid black;
      position: relative;
      overflow: hidden;
    }

    .bike {
      width: 50px;
      height: 30px;
      background-color: red;
      position: absolute;
    }
  </style>
</head>
<body>
  <h1>Bike Race Game</h1>

  <div id="game-container">
    <div id="bike" class="bike"></div>
  </div>

  <script>
    // JavaScript code for the game
    document.addEventListener("DOMContentLoaded", function() {
      var bike = document.getElementById("bike");
      var gameContainer = document.getElementById("game-container");

      // Initial bike position
      var bikeX = 0;
      var bikeY = 200;

      // Move the bike
      function moveBike(event) {
        if (event.key === "ArrowUp") {
          bikeY -= 10;
        } else if (event.key === "ArrowDown") {
          bikeY += 10;
        } else if (event.key === "ArrowLeft") {
          bikeX -= 10;
        } else if (event.key === "ArrowRight") {
          bikeX += 10;
        }

        // Update bike position
        bike.style.top = bikeY + "px";
        bike.style.left = bikeX + "px";
      }

      // Add event listener for keydown event
      document.addEventListener("keydown", moveBike);
    });
  </script>
</body>
</html>
