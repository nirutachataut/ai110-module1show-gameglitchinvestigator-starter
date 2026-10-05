# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

When I first ran the game, it looked functional, but several parts of the logic were not working correctly. One of the first bugs I noticed was that the hint direction was backwards, so when my guess was too high, the game told me to go higher instead of lower. I also noticed that the difficulty range could say 1–50, but the secret number could still be outside that range, such as 98. Another problem was that the attempt counter started as if one attempt had already been used.

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| Guess higher than the secret number | Game should say the guess is too high and tell me to go lower | Game said "Too High" but told me to go higher | No console error |
| Selected Hard difficulty with range 1–50 and started a new game | Secret number should be between 1 and 50 | Developer Debug Info showed a secret number of 98 | No console error |
| Started the game without making a guess | Attempts used should start at 0 | The game started with the attempt counter already at 1 | No console error |

---

## 2. How did you use AI as a teammate?

I used ChatGPT and GitHub Copilot to help me understand the code and connect the bugs I saw in the game to the functions causing them. One AI suggestion I accepted was fixing the hint logic in `check_guess()` so that a guess above the secret told the player to go lower, and I verified it by testing guesses above and below the secret number in the app. I also used Copilot in VS Code with `app.py` and `logic_utils.py` attached to trace why Hard mode showed a range of 1–50 while the stored secret could still be outside that range. One AI suggestion I rejected was a bigger refactor that moved extra functions and reshaped the game more broadly; I changed that idea because I wanted to keep the original structure and make only the specific fixes needed for the bugs. After comparing the suggestion to the actual code, I kept the smaller, safer edits and re-ran the game to confirm the fixes worked.

---

## 3. Debugging and testing your fixes

I verified each fix by replaying the original bug scenarios in the Streamlit app and checking whether the UI behavior matched the expected outcome. I manually tested Hard mode to confirm the secret stayed within the 1–50 range, tried guesses above and below the target to confirm the hints pointed in the right direction, and checked that the attempt counter started at zero. After the app-level checks passed, I ran `pytest` to confirm the refactored logic still met the test suite and did not introduce regressions. Seeing both the manual Streamlit checks and the automated tests agree gave me confidence that the fixes were reliable.

---

## 4. What did you learn about Streamlit and state?

I learned that Streamlit reruns the Python script whenever the user interacts with something like a button, checkbox, or select box. Because the script runs again, normal variables can reset, so `st.session_state` is used to keep important values such as the secret number, score, attempts, and game status between reruns. I would explain it as Streamlit refreshing the program after an interaction, while session state acts like memory that keeps the game from starting over every time.

---

## 5. Looking ahead: your developer habits

One habit I want to reuse is testing one bug at a time and reproducing the exact problem before changing the code. Next time I use AI for coding, I would be more specific about asking for small fixes instead of accepting a full rewrite, because keeping the original structure made it easier for me to understand what changed. This project showed me that AI-generated code can look correct and still contain logical bugs, so I should always test the code myself instead of assuming it works.
