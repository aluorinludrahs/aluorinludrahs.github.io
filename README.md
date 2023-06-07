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

    .obstacle {
      width: 30px;
      height: 30px;
      background-color: black;
      position: absolute;
    }

    #score {
      font-size: 24px;
    }
  </style>
</head>
<body>
  <h1>Bike Race Game</h1>

  <div id="game-container">
    <div id="bike" class="bike"></div>
    <div id="score">Score: 0</div>
  </div>

  <script>
    // JavaScript code for the game
    document.addEventListener("DOMContentLoaded", function() {
      var bike = document.getElementById("bike");
      var gameContainer = document.getElementById("game-container");
      var scoreElement = document.getElementById("score");

      var bikeX = 0;
      var bikeY = 200;
      var score = 0;
      var obstacleInterval;
      var level = 1;

      // Function to move the bike
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

        // Check collision with obstacles
        var obstacles = document.getElementsByClassName("obstacle");
        for (var i = 0; i < obstacles.length; i++) {
          var obstacle = obstacles[i];
          if (isColliding(bike, obstacle)) {
            endGame();
            break;
          }
        }
      }

      // Function to generate obstacles
      function generateObstacles() {
        var obstacle = document.createElement("div");
        obstacle.className = "obstacle";
        obstacle.style.top = getRandomPosition() + "px";
        obstacle.style.left = gameContainer.offsetWidth + "px";
        gameContainer.appendChild(obstacle);

        // Animate the obstacle
        var obstacleAnimation = setInterval(function() {
          obstacle.style.left = parseInt(obstacle.style.left) - 5 + "px";

          // Check if obstacle is out of the game container
          if (parseInt(obstacle.style.left) < -obstacle.offsetWidth) {
            clearInterval(obstacleAnimation);
            gameContainer.removeChild(obstacle);
          }
        }, 10);
      }

      // Function to check collision between two elements
      function isColliding(element1, element2) {
        var rect1 = element1.getBoundingClientRect();
        var rect2 = element2.getBoundingClientRect();

        return !(
          rect1.top > rect2.bottom ||
          rect1.right < rect2.left ||
          rect1.bottom < rect2.top ||
          rect1.left > rect2.right
        );
      }

      // Function to end the game
      function endGame() {
        clearInterval(obstacleInterval);
        document.removeEventListener("keydown", moveBike);
        alert("Game Over! Final Score: " + score);
      }

      // Function to update score
      function updateScore() {
        score++;
        scoreElement.textContent = "Score: " + score;
      }

      // Function to get random Y position for obstacles
      function getRandomPosition() {
        var minHeight = 30;
        var maxHeight = gameContainer.offsetHeight - minHeight;
        return Math.floor(Math.random() * (maxHeight - minHeight + 1)) + minHeight;
      }

      // Add event listener for keydown event
      document.addEventListener("keydown", moveBike);

      // Start the game
      obstacleInterval = setInterval(function() {
        generateObstacles();
        updateScore();

        // Increase level every 10 seconds
        if (score % 10 === 0) {
          level++;
          clearInterval(obstacleInterval);
          obstacleInterval = setInterval(generateObstacles, 1000 - (level * 100));
        }
      }, 1000);
    });
  </script>
</body>
</html>
