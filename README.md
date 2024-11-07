<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Pop-up Game</title>
    <style>
        /* Body Style */
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #fff0f5; /* Soft pink background */
            background-image: url('https://upload.wikimedia.org/wikipedia/commons/thumb/1/1e/Red_heart.svg/512px-Red_heart.svg.png'), 
                              url('https://upload.wikimedia.org/wikipedia/commons/e/ec/Yellow_duck_%28cartoon_style%29.svg'); /* Cute hearts and ducks */
            background-repeat: repeat, repeat;
            background-position: top left, bottom right;
            background-size: 100px 100px, 80px 80px; /* Size of hearts and ducks */
        }

        /* Popup Box */
        .popup {
            background-color: #fff;
            border-radius: 15px;
            padding: 40px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
            text-align: center;
            display: none;
            width: 350px;
            position: relative;
            z-index: 2;
            font-size: 18px;
            color: #ff66b3; /* Pink text */
            font-family: 'Verdana', sans-serif;
        }

        /* Popup Header */
        .popup h3 {
            background-color: #ff66b3; /* Pink background */
            color: white;
            margin: -40px -40px 20px -40px; /* Adjusted to create rounded corners */
            padding: 20px;
            font-size: 20px;
            font-weight: bold;
            border-radius: 15px 15px 0 0;
        }

        /* Button Style */
        button {
            padding: 12px 24px;
            margin: 10px;
            cursor: pointer;
            border: none;
            background-color: #ff8cd7; /* Soft pink button */
            color: white;
            font-size: 16px;
            border-radius: 30px;
            transition: all 0.3s ease;
        }

        button:hover {
            background-color: #ff66b3; /* Darker pink when hovering */
            transform: scale(1.05); /* Slightly bigger when hovered */
        }

        .final-message {
            font-size: 22px;
            font-weight: bold;
            color: #ff66b3; /* Pink for success message */
            margin-top: 20px;
        }

        .incorrect {
            color: #ff5050; /* Red for incorrect answers */
        }

    </style>
</head>
<body>

    <!-- Popup: Will you go on a date with me? -->
    <div id="popup2" class="popup" style="display: block;">
        <h3>Will you go on a date with me?</h3>
        <button onclick="handleAnswer('yes')">Yes</button>
        <button id="noButton" onclick="handleNoClick()">No</button>
    </div>

    <div id="result" class="popup">
        <p id="message"></p>
        <button onclick="restartGame()">Play Again</button>
    </div>

    <script>
        // Function to handle the welcome message fade-out
        setTimeout(function() {
            document.getElementById("welcomeMessage").style.opacity = "0"; // Fade it out
        }, 3000); // It will fade out after 3 seconds

        function handleAnswer(answer) {
            if (answer === 'yes') {
                // Display the message when "Yes" is clicked
                document.getElementById("message").innerHTML = "I knew you would say YES ❤️🥰🫂";
                document.getElementById("message").classList.add('final-message');
                document.getElementById("popup2").style.display = "none";
            }
            document.getElementById("result").style.display = "block";
        }

        // Function to make the "No" button run away
        function handleNoClick() {
            const noButton = document.getElementById("noButton");

            // Randomly position the "No" button in a different spot
            const maxX = window.innerWidth - noButton.offsetWidth;
            const maxY = window.innerHeight - noButton.offsetHeight;

            const randomX = Math.random() * maxX;
            const randomY = Math.random() * maxY;

            noButton.style.position = 'absolute';
            noButton.style.left = randomX + 'px';
            noButton.style.top = randomY + 'px';
        }

        function restartGame() {
            // Reset the game
            document.getElementById("popup2").style.display = "block";
            document.getElementById("result").style.display = "none";
            document.getElementById("message").innerHTML = "";
        }
    </script>
</body>
</html>
