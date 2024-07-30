# Guess My Number Game

This repository contains a simple number guessing game built with HTML, CSS, and JavaScript. The objective of the game is to guess a randomly generated secret number between 1 and 20. [TRY NOW!](https://qyuzet.github.io/js-guess-my-number-game)

## Features

- Responsive user interface
- Random number generation
- Score tracking
- High score tracking
- Interactive feedback messages

## Live Demo

Check out the live demo [here](https://qyuzet.github.io/js-guess-my-number-game).

## How to Play

1. Enter a number between 1 and 20.
2. Click the "Check!" button.
3. Receive feedback on whether your guess is too high, too low, or correct.
4. Keep guessing until you find the secret number or your score reaches 0.
5. Try to beat your high score!

## JavaScript Explanation

### Variable Initialization

```javascript
let secretNumber = Math.trunc(Math.random() * 20) + 1;
let score = 20;
let highscore = 0;
```

- `secretNumber`: Random number between 1 and 20.
- `score`: Player's current score.
- `highscore`: Highest score achieved.

### Display Message Function

```javascript
const displayMessage = function (message) {
  document.querySelector('.message').textContent = message;
};
```

- `displayMessage`: Updates the message displayed to the player.

### Event Listener for Check Button

```javascript
document.querySelector('.check').addEventListener('click', function () {
  const guess = Number(document.querySelector('.guess').value);
  // Game logic...
});
```

- Adds a click event listener to the "Check!" button.
- Reads the player's guess from the input field.

### Game Logic

```javascript
if (!guess) {
  displayMessage('⛔️ No number!');
} else if (guess === secretNumber) {
  displayMessage('🎉 Correct Number!');
  document.querySelector('body').style.backgroundColor = '#60b347';
  document.querySelector('.number').textContent = secretNumber;
  if (score > highscore) {
    highscore = score;
    document.querySelector('.highscore').textContent = highscore;
  }
} else if (guess !== secretNumber) {
  if (score > 1) {
    displayMessage(guess > secretNumber ? '📈 Too high!' : '📉 Too low!');
    score--;
    document.querySelector('.score').textContent = score;
  } else {
    displayMessage('💥 You lost the game!');
    document.querySelector('.score').textContent = 0;
  }
}
```

- Checks if the input is valid.
- Compares the player's guess to the secret number.
- Updates the message, score, and background color based on the guess.
- Tracks and updates the high score.

### Event Listener for Again Button

```javascript
document.querySelector('.again').addEventListener('click', function () {
  score = 20;
  secretNumber = Math.trunc(Math.random() * 20) + 1;
  displayMessage('Start guessing...');
  document.querySelector('.score').textContent = score;
  document.querySelector('.number').textContent = '?';
  document.querySelector('.guess').value = '';
  document.querySelector('body').style.backgroundColor = '#222';
});
```

- Resets the game state when the "Again!" button is clicked.

## How to Run

1. Clone this repository.
2. Open `index.html` in your web browser.

## Contributing

Feel free to submit issues or pull requests for improvements and bug fixes.

## License

This project is licensed under the MIT License.
