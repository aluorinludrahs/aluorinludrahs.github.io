# Import the necessary libraries
import pygame
import random

# Initialize the pygame library
pygame.init()

# Create the screen
screen = pygame.display.set_mode((600, 400))

# Create the background image
background = pygame.image.load("background.png")

# Create the bike sprite
bike = pygame.image.load("bike.png")

# Create the obstacles
obstacles = []
for i in range(10):
    obstacles.append(pygame.image.load("obstacle.png"))

# Create the score
score = 0

# Create the game loop
while True:
    # Handle events
    for event in pygame.event.get():
        # Quit the game if the user clicks the close button
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Update the bike position
    bike_x = bike_x + 5

    # Check if the bike has hit an obstacle
    for obstacle in obstacles:
        if bike.colliderect(obstacle):
            # Game over!
            print("Game over!")
            break

    # Update the obstacles position
    for obstacle in obstacles:
        obstacle_x = obstacle_x - 5

    # Remove obstacles that have gone off the screen
    for obstacle in obstacles:
        if obstacle_x < -100:
            obstacles.remove(obstacle)

    # Add new obstacles
    if len(obstacles) < 10:
        obstacles.append(pygame.image.load("obstacle.png"))

    # Update the score
    score = score + 1

    # Draw the background image
    screen.blit(background, (0, 0))

    # Draw the bike sprite
    screen.blit(bike, (bike_x, 200))

    # Draw the obstacles
    for obstacle in obstacles:
        screen.blit(obstacle, (obstacle_x, 0))

    # Draw the score
    text = "Score: " + str(score)
    pygame.draw.rect(screen, (0, 0, 0), (0, 0, 100, 20))
    pygame.draw.text(screen, text, (10, 10), (255, 255, 255))

    # Update the display
    pygame.display.update()
