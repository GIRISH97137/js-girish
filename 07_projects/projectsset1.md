#Projects related to DOM


##project link
[click here ] 

# Solution code 

## project 1 Color-Changer
 

```javascript


console.log("Girish")

const buttons = document.querySelectorAll('.button');
console.log(buttons);

const body = document.querySelector('body');

buttons.forEach(function (button) {
  console.log(button);
  button.addEventListener('click', function (e) {
    console.log(e);
    console.log(e.target);
    if (e.target.id === 'grey') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'white') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'blue') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'yellow') {
      body.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'purple') {
      body.style.backgroundColor = e.target.id;
    }

  });
});


```



## project 2 BMI Calculator

```javascript 
 


const form = document.querySelector('form');
//this usecase will give you empty
//const height = parseInt(document.querySelector('#height').value);

form.addEventListener('submit', function (e) {
  e.preventDefault();

  const height = parseInt(document.querySelector('#height').value);
  const weight = parseInt(document.querySelector('#weight').value);
  const results = document.querySelector('#results');


  if (height === '' || height < 0 || isNaN(height)) {
    results.innerHTML = `please give a valid height ${height}`;
  }

  if (weight === '' || weight < 0 || isNaN(weight)) {
    results.innerHTML = `please give a valid weight ${weight}`;
  } else {
   const bmi =  weight / ((height * height) / 10000).toFixed(2);

    //show result

    results.innerHTML = `<span>${bmi}</span>`;
  }
});



```
## project 3 clock

```javascript

const clock = document.getElementById('clock')

//const clock = document.querySelector('clock')


setInterval(function(){
  let date = new Date()
  //console.log(date.toLocaleTimeString())
  clock.innerHTML = date.toLocaleTimeString();
}, 1000)

```

## project 4  Game - Guess the Number

```javascript

let randomNumber = parseInt(Math.random() * 100 + 1);
//console.log(randomNumber)
const submit = document.querySelector('#subt');
const userInput = document.querySelector('#guessField');

const guesSlot = document.querySelector('.guesses');
const remaining = document.querySelector('.lastResult');

const lowOrHi = document.querySelector('.lowOrHi');
const startOver = document.querySelector('.resultParas');

const p = document.createElement('p');

let prevGuess = [];
let numGuess = 1;

let playGame = true;

if (playGame) {
  submit.addEventListener('click', function (e) {
    e.preventDefault();

    let guess = parseInt(userInput.value);
    console.log(guess);
    validateGuess(guess);
  });
}

function validateGuess(guess) {
  //validation
  console.log(guess);
  if (isNaN(guess)) {
    alert('please enter valid number');
  } else if (guess < 1) {
    alert('enter number greater than 1');
  } else if (guess > 100) {
    alert('enter number less than 100');
  } else {
    prevGuess.push(guess);
    if (numGuess === 11) {
      displayGuess(guess);
      displayMessage(`Game Over. Random number was  ${randomNumber}`);
      endGame();
    } else {
      displayGuess(guess);
      checkGuess(guess);
    }
  }
}

function checkGuess(guess) {
  //check

  if (guess === randomNumber) {
    displayMessage(`Correct Guess`);
    endGame();
  } else if (guess < randomNumber) {
    displayMessage(`low number `);
  } else if (guess > randomNumber) {
    displayMessage(`high number, guess more .....`);
  }
}

function displayGuess(guess) {
  userInput.value = '';
  guesSlot.innerHTML += `${guess}   `;
  numGuess++;
  remaining.innerHTML = `${11 - numGuess}  `;
}

function displayMessage(msg) {
  //
  lowOrHi.innerHTML = `<h2>${msg}</h2>`;
}

function endGame() {
  //
  userInput.value = '';
  userInput.setAttribute('disabled', '');
  p.classList.add('button');
  p.innerHTML = `<h2 id="newGame">Start new Game</h2>`;
  startOver.appendChild(p);
  playGame = false;
  newGame();
}

function newGame() {
  const newGameButton = document.querySelector('#newGame');

  newGameButton.addEventListener('click', function (e) {
    randomNumber = parseInt(Math.random() * 100 + 1);
    prevGuess = [];
    numGuess = 1;
    guesSlot.innerHTML = '';
    remaining.innerHTML = `${11 - numGuess}`;
    userInput.removeAttribute('disabled');
    startOver.removeChild(p);

    playGame = true;
  });
}


```