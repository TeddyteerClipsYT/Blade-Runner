# Blade-Runner
// Define canvas dimensions
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
canvas.width = 800;
canvas.height = 600;

// Load game assets
const playerImg = new Image();
playerImg.src = 'assets/player.png';
const katanaImg = new Image();
katanaImg.src = 'assets/katana.png';

// Define player and weapon positions
let playerX = 50;
let playerY = 50;
let katanaX = 700;
let katanaY = 400;

// Detect player keyboard input
document.addEventListener('keydown', function(event) {
  if (event.code === 'ArrowRight') {
    playerX += 10;
  }
  else if (event.code === 'ArrowLeft') {
    playerX -= 10;
  }
  else if (event.code === 'ArrowDown') {
    playerY += 10;
  }
  else if (event.code === 'ArrowUp') {
    playerY -= 10;
  }
  
  // Check for weapon collision
  if (playerX + playerImg.width >= katanaX &&
      playerX <= katanaX + katanaImg.width &&
      playerY + playerImg.height >= katanaY &&
      playerY <= katanaY + katanaImg.height) {
        alert('You just picked up a katana!');
        // Code to equip katana as player's weapon goes here
      }
});

// Render the game on the canvas
function render() {
  // Clear the canvas
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  
  // Draw the player and the katana
  ctx.drawImage(playerImg, playerX, playerY);
  ctx.drawImage(katanaImg, katanaX, katanaY);
  
  // Request the next frame
  requestAnimationFrame(render);
}

// Start the game loop
requestAnimationFrame(render);
 }
 # Define a dictionary to store user information
users = {}

# Prompt the user for their choice and username
choice = input("Do you want to register (r) or sign in (s)? ")
username = input("Please enter your username: ")

# Process the user's choice
if choice == 'r':
  # Register a new user
  if username in users:
    print("Error: username already exists!")
  else:
    users[username] = {"password": input("Please enter a password: ")}
    print("User registered successfully!")
elif choice == 's':
  # Sign in an existing user
  if username not in users:
    print("Error: username not found!")
  else:
    password = input("Please enter your password: ")
    if password != users[username]["password"]:
      print("Error: incorrect password!")
    else:
      print("Welcome back, " + username + "!")
else:
  print("Error: invalid choice!")

