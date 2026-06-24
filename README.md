# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [ ] Describe the game's purpose.
The purpose of the game was to challenge the player to find the right number by giving secret numberes and hints with too high or too low within a limited number of attempts. 

- [ ] Detail which bugs you found.
1. The hint logic was reversed. I put 31, when the secret number was 41, and instead of telling me to "GO HIGHER" it said "GO LOWER" 
2. When I would click new game after finishing one of them, it wouldn't reset 
3. The attempt would stay at 1, when the attempt should've been 0 because the game didnt start yet. Showing an inaccurate number of attempts

- [ ] Explain what fixes you applied.
changed 3 functions and 
1. Correcte the logic in check_guess function, so that guesses below secret number can say "GO HIGHER" and above that say "GO LOWER" 
2. Updated the New Game mode so it reset and it made it reset everything such as attempts, status, score, history, and secret number
3. Fixed the attempt tracker so that it counts and correctly reflects the correct number of attempts made by the player

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. User has to enter a value in the text box
2. User enters 31
3. The game returns "TOO HIGH" as the number is higher than the secret number
4. The score and the atempt updates after entering the value 
5. User guesses another number close to the actual number
6. Game provides another hint
7. User enters the right number
8. Game displays winning message and final score
9. User clicks "New Game"
10. Resets the game with new secret number and reset score

**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results

```
# Paste your pytest output here, e.g.:
# pytest tests/
# ========================= X passed in 0.XXs =========================
```

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
