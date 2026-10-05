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

- The purpose of the game is to guess a randomly generated secret number within the selected difficulty range.
- The main bugs I found were backwards hint directions, a secret number that could fall outside the displayed difficulty range, and an attempt counter that started incorrectly.
- I fixed the hint logic, corrected the difficulty-based secret generation, reset the attempt counter properly, and moved `check_guess()` and `parse_guess()` into `logic_utils.py`.
- I also added pytest coverage for the guessing logic and manually tested the game in Streamlit after the fixes.

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. The user selects a difficulty, for example Hard mode, which uses a range of 1 to 50.
2. The game generates a secret number within that range.
3. The user enters a guess lower than the secret number, and the game displays "Too Low" and tells the user to go HIGHER.
4. The user enters a guess higher than the secret number, and the game displays "Too High" and tells the user to go LOWER.
5. The score and attempt count update after each valid guess.
6. When the user enters the correct number, the game displays "Correct!" and shows the final score.
7. If the user uses all allowed attempts without guessing correctly, the game ends and shows the secret number.

**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results

```
================================================================ test session starts ================================================================
platform darwin -- Python 3.11.9, pytest-9.1.1, pluggy-1.6.0
rootdir: /Users/nirutachataut/ai110-module1show-gameglitchinvestigator-starter
plugins: anyio-4.15.1
collected 3 items                                                                                                                                   

tests/test_game_logic.py ...                                                                                                                  [100%]

================================================================= 3 passed in 0.03s =================================================================
```

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
