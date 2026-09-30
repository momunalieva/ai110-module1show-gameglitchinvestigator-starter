# 💭 Reflection: Game Glitch Investigator

## 1. What was broken when you started?

When I first opened the game, I started by playing with it and trying different numbers to understand what was wrong. I noticed that the hints did not make sense. When my number was too high, the game told me to go higher instead of lower. I also noticed that the New Game button was not fully starting a new game, the attempts were not counted correctly, and I could enter numbers outside of the range.

**Bug Reproduction Log**

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| Guess 60 when secret is 50 | Tell me the guess is too high and to go lower | It said Too High but told me to go HIGHER | No error |
| Click New Game after finishing a game | Start a completely new game | Some information from the old game was still there | No error |
| Enter a number outside the range | Tell me to enter a number inside the range | The game accepted numbers outside the range | No error |
| Start a Normal game | Give me 8 attempts | The attempt count started at 1 | No error |

---

## 2. How did you use AI as a teammate?

I used ChatGPT and the AI assistant in VS Code to help me understand the code and find where the problems were. I did not want to change everything at once, so I tried to work on one problem at a time. AI helped me move the main game functions from `app.py` to `logic_utils.py` and helped me fix the higher and lower hints. I checked the changes myself by running the game and trying different guesses.

One problem happened when I was moving the functions. I accidentally deleted too much code from `app.py`. Instead of continuing with that change, I used Undo, brought the original code back, and then removed only the functions that needed to be moved. This helped me understand that I should check the code after every AI suggestion and not just accept everything without looking at it.

---

## 3. Debugging and testing your fixes

My main way of checking the fixes was to run the game and try the same problems again. For example, if the secret was 50, I checked that 60 said "Too High" and "Go LOWER," and 40 said "Too Low" and "Go HIGHER." I also tested the New Game button, the attempt count, numbers outside of the allowed range, and the game history.

AI helped me make pytest tests for the game logic. At first the tests failed because the old tests expected only one result, but `check_guess` was returning both the outcome and the message. I changed the tests to check both values. I also had an import problem where pytest could not find `logic_utils.py`, so I added an empty `__init__.py` file inside the `tests` folder. After fixing these problems, I ran `pytest` again and all 3 tests passed.

---

## 4. What did you learn about Streamlit and state?

I learned that Streamlit runs the code again when I click something or enter a guess. At first this was confusing because I thought the program would just continue from the same place. I learned that `st.session_state` is what keeps information like the secret number, attempts, score, game status, and history when Streamlit runs the page again. I would explain session state as the memory of the game.

---

## 5. Looking ahead: your developer habits

One thing I learned from this project is to make small changes and test them before moving to the next thing. When something did not work, I looked at the error, tried to understand what it was saying, and then fixed that specific problem. I also learned that tests are useful because at the end I could run `pytest` and see `3 passed`, which gave me more confidence that the main game logic was working.

Next time I use AI for coding, I will check the changes more carefully before deleting or replacing a big part of my code. This project showed me that AI can help me find problems and explain code, but I still need to run the program, check the result, and decide if the change actually makes sense.