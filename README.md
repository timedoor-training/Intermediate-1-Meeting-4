# Timedoor Training Teen
## Intermediate A - Meeting 4

Pertemuan 4 mempelajari conditional logic 
- If statement
- Else If Statement
- Elese Statement

Contoh aplikasi yang akan dibuat :
>https://timedoor-guessinggame.netlify.app/

untuk memulai pembuatan aplikasi download terlebih dahulu di dalam repo
>https://github.com/timedoorAcademy-smp/guessGame_js



###  HTML Code Basic

```html
<body>
    <h1>Guess The Number</h1>
    <p>We have selected a random number between 1 - 10.
        See if you can guess it.</p>
    <div id="wrapper">
        <div class="form">
            <label for="guessField" id="guesses">Enter a guess: </label>
            <input type="number" id="guessField" class="guessField">
            <input type="submit" value="Submit guess" class="guessSubmit" id="submitguess">
        </div>
        <div class="resultParas">
            <p>Guesses Remaining: <span class="lastResult">10</span></p>
            <p>Result : <span class="resultCheck"></span></p>
        </div>
    </div>

</body>
```

### CSS Basic
```html
<style>
    html {
        font-family: "Comic Sans MS", "Comic Sans", cursive;
    }

    h1 {
        background-color: #17A589;
        color: #fff;
        text-align: center;
        width: 750px;
    }

    p {
        font-size: 18px;
        text-align: center;
    }

    body {
        width: 100%;
        max-width: 750px;
        min-width: 480px;
        margin: 0 auto;
    }

    #wrapper {
        box-sizing: border-box;
        text-align: center;
        width: 750px;
        height: 400px;
        background-color: #17A589;
        color: #fff;
        font-size: 25px;
    }

    #submitguess {
        background-color: yellow;
        color: black;
        width: 200px;
        height: 50px;
        border-radius: 25px;
        font-size: 30px;
        border-style: none;
        margin-top: 50px;
        /* margin-left: 75px; */
    }

    #guessField {
        color: #000;
        width: 550px;
        height: 100px;
        font-size: 30px;
        border-style: none;
        margin-top: 25px;
        font-size: 45px;
        /* margin-left: 50px; */
        border: 5px solid #14727d;
        text-align: center;
    }

    #guess {
        font-size: 55px;
        /* margin-left: 90px; */
        margin-top: 120px;
        color: #fff;
    }

    .resultCheck {
        color: yellow;
        padding: 7px;
        font-size: 24px;
    }
</style>
```

### Javascript Basic
```html
    <script type="text/javascript">
        const numberInputed = document.querySelector('#guessField');
        const guessSlot = document.querySelector('.lastResult');
        const resultCheck = document.querySelector('.resultCheck');
        const p = document.createElement('p');

        //1. Set Variable  
        var randomNumber = parseInt((Math.random() * 10) + 1)
        var guessCount = 10

        document.getElementById("submitguess").onclick = function () {
            // 2. Event when Guess Submited
            var guess = numberInputed.value;
            validateGuess(guess)
        }

        function validateGuess(guess) {
            //3. Function to validate the guess
            if (guess < 1) {
                alert(`Please enter a number greater than 0!`)
            } else if (guess > 10) {
                alert(`Please enter a number less than 11!`)
            } else if (guessCount === 0) {
                displayMessage("Game Over!!!")
                endGame();
            } else {
                checkGuess(guess)
            }
        }
        function checkGuess(guess) {
            //4. Function to check the Guess
            if (guess == randomNumber) {
                displayMessage("Congrats!!")
                endGame()
            } else if (guess > randomNumber) {
                guessCount--;
                displayMessage("oops!try smaller number!")
            } else if (guess < randomNumber) {
                guessCount--
                displayMessage("Opps!Try greater number!")
            }
        }

        function endGame() {
            //5. Function to end the Game
            numberInputed.value = " "
            document.getElementById("submitguess").setAttribute("disabled,' '")
        }

        function displayMessage(message) {
            resultCheck.innerHTML = `<b>${message}</b>`
            guessSlot.innerHTML = `${guessCount}  `;
        }


    </script>
```
