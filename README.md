# **Pig Game**  
#### Inspired by [Jonas Schmedtmann](https://github.com/jonasschmedtmann) || See it live at [CodePen](https://codepen.io/shady-ashraf/pen/dPboXYa)
##### Classic Two-Player Dice Game Implementation  
###### This project demonstrates an interactive, two-player dice game built using HTML, CSS, and JavaScript. The goal is to reach a score of 100 before your opponent, with strategic decisions on when to "roll" or "hold" the dice.  

---

## **Table of Contents**  
- [Overview](#overview)  
- [Game Rules](#game-rules)  
- [Features](#features)  
- [File Structure](#file-structure)  
- [HTML Details](#html-details)  
- [CSS Styling](#css-styling)  
- [JavaScript Logic](#javascript-logic)  
- [Deployment](#deployment)  
- [Selectors Used in the Project](#selectors-used-in-the-project)  

---

## **Overview**  
The **Pig Game Project** is a fun and interactive game designed to enhance JavaScript programming skills by integrating DOM manipulation and event handling.

**Technologies used:**  
- HTML5  
- CSS3  
- JavaScript (ES6)  

---

## **Game Rules**  
1. Players take turns to roll a dice.  
2. Rolling a "1" switches turns, and the current score resets to 0.  
3. Players can choose to "hold" their score, adding the current score to their total and switching turns.  
4. The first player to reach 100 wins the game.  

---

## **Features**  
- **Dynamic Gameplay**: Players can roll dice, accumulate scores, and switch turns seamlessly.  
- **Winner Highlighting**: The winning player is visually indicated with a special style.  
- **New Game Reset**: Players can reset the game at any point.  
- **Responsive UI**: Adjusts for various screen sizes using modern CSS.  

---

## **File Structure**  
```plaintext  
pig-game/  
├── index.html  
├── style.css  
└── script.js  
```  

---

## **HTML Details**  
The HTML file (`index.html`) structures the game layout with players' panels, buttons, and a dice image.

### Key Sections:  
1. **Player Panels**:  
   Two player sections track each player's scores and active status.  
   ```html  
   <section class="player player--0 player--active">  
     <h2 class="name" id="name--0">Player 1</h2>  
     <p class="score" id="score--0">43</p>  
     <div class="current">  
       <p class="current-label">Current</p>  
       <p class="current-score" id="current--0">0</p>  
     </div>  
   </section>  
   ```  

2. **Dice Display**:  
   Displays the dice roll result dynamically.  
   ```html  
   <img src="dice-5.png" alt="Playing dice" class="dice" />  
   ```  

3. **Action Buttons**:  
   Buttons for rolling dice, holding the score, and starting a new game.  
   ```html  
   <button class="btn btn--new">🔄 New game</button>  
   <button class="btn btn--roll">🎲 Roll dice</button>  
   <button class="btn btn--hold">📥 Hold</button>  
   ```  

---

## **CSS Styling**  
The CSS file (`style.css`) ensures a visually appealing and responsive design.  

### Key Styles:  
- **Player Panels**:  
  - Active and winning players are visually distinguished using dynamic styles.  
- **Dice and Buttons**:  
  - Dice rolls are highlighted, and buttons are styled for clarity and interactivity.  

### Snippet:  
```css  
.player--active {  
  background-color: rgba(255, 255, 255, 0.4);  
}  

.player--winner {  
  background-color: #2f2f2f;  
}  

.btn {  
  background-color: white;  
  padding: 0.7rem 2.5rem;  
  border-radius: 50rem;  
  cursor: pointer;  
}  

.dice {  
  position: absolute;  
  height: 10rem;  
  box-shadow: 0 2rem 5rem rgba(0, 0, 0, 0.2);  
}  
```  

---

## **JavaScript Logic**  
The JavaScript file (`script.js`) manages game dynamics with clear and concise logic.  

### Key Functions:  
1. **Initialization (`init`)**:  
   Resets the game state and updates the UI.  
   ```javascript  
   const init = function () {  
     scores = [0, 0];  
     currentScore = 0;  
     activePlayer = 0;  
     playing = true;  

     score0El.textContent = 0;  
     score1El.textContent = 0;  
     current0El.textContent = 0;  
     current1El.textContent = 0;  
     diceEl.classList.add("hidden");  
     player0El.classList.add("player--active");  
   };  
   ```  

2. **Rolling the Dice**:  
   Generates a random dice roll and updates the current score unless a "1" is rolled.  
   ```javascript  
   btnRoll.addEventListener("click", function () {  
     if (playing) {  
       const dice = Math.trunc(Math.random() * 6) + 1;  
       diceEl.src = `dice-${dice}.png`;  
       if (dice !== 1) {  
         currentScore += dice;  
         document.getElementById(`current--${activePlayer}`).textContent =  
           currentScore;  
       } else {  
         switchPlayer();  
       }  
     }  
   });  
   ```  

3. **Holding the Score**:  
   Adds the current score to the total and checks for a winner.  
   ```javascript  
   btnHold.addEventListener("click", function () {  
     if (playing) {  
       scores[activePlayer] += currentScore;  
       if (scores[activePlayer] >= 100) {  
         document  
           .querySelector(`.player--${activePlayer}`)  
           .classList.add("player--winner");  
       } else {  
         switchPlayer();  
       }  
     }  
   });  
   ```  

---

## **Deployment**  
1. Clone the repository:  
   ```bash  
   git clone https://github.com/shadyashraf174/Pig-Game.git  
   ```  
2. Open `index.html` in a browser to start playing.  

---

## **Selectors Used in the Project**  

### **HTML Selectors**  
- **Element Selectors**:  
  - `<section>`: Player panels.  
  - `<button>`: Action buttons.  

- **Class Selectors**:  
  - `.player--active`: Highlights the active player.  
  - `.player--winner`: Indicates the winning player.  

### **CSS Selectors**  
- **Pseudo-classes**:  
  - `:active`: Button press effects.  
- **Dynamic Styling**:  
  - `hidden` class toggles the dice's visibility.  

---  

![Screenshot 2024-12-01 151155](https://github.com/user-attachments/assets/7e7fcb03-2380-4d2b-8710-1cf43dd66d56)
![Screenshot 2024-12-01 151248](https://github.com/user-attachments/assets/47ff2955-f8f8-4edc-bc66-1b3e4f7b0704)
![Screenshot 2024-12-01 151322](https://github.com/user-attachments/assets/b061917c-ba83-4a8b-b933-b06d90bc3bae)

Ready to play? Have fun strategizing your way to victory! 🎲
