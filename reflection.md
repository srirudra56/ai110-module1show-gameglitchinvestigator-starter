# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it? It had three difficulty levels(Easy, Normal, Difficult). We have to enter a number into the text box where it says Enter your guess. There are secret numbers present, shows the number of attempts, the score, the difficulty, and tracks the history. 

- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards"). when I put 31, the secret number was 41 and it said go lower instead of go higher. When I click new game, it would not 

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input               |     Expected Behavior             |     Actual Behavior   |    Console Output / Error |
|---------------------|---------------------------|-----------------------|---------------------------|
|Guess:31             |        GO HIGHER                 GO LOWER                     None            |
|click new game       | A fresh game should start | game wont reset       |           None            |
|Start a new game     | Attempt should begin 1 after first try | Attempt starts at 0 |  None          |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)? ChatGPT

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result). 
I asked the ChatGPT why guessing 31, when the secret was 41, showed "GO LOWER" instead of "GO HIGHER." Chat explained that the high/low messages in `check_guess` were reversed. Such as guess is somehow greater than hint and prints GO HIGHER. It also pointed out that the code sometimes converts the secret number to a string based on the attempt number, which can cause unreliable comparisons.

- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result). 
One AI suggestion that was misleading was that the score calculation was definitely a bug because the score jumped from -5 to 55 after a correct guess. After reviewing the code and testing the game, I realized that the score increase came from the `update_score` function, which intentionally awards a large bonus for winning. Although the scoring system seemed unusual, it was not necessarily broken. I verified this by reading the scoring logic in the code and comparing the calculated score to the game's output.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
I verified my fixes by running the Streamlit app again and testing the same bug from the first case. When the secret number was 41 and I guessed 31, the game correctly displayed "Go HIGHER." When I guessed a number above the secret, the game displayed "Go LOWER." I also won the game, clicked New Game, and confirmed that the game reset properly and accepted a new guess instead of showing the old "You already won" message.

- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
  One manual test I ran was setting the secret number to 41 and entering a guess of 31. Before the fix, the game incorrectly displayed "Go LOWER." After updating the check_guess logic, the game correctly displayed "Go HIGHER." This showed me that the hint logic was working properly after the repair.

- Did AI help you design or understand any tests? How?
AI helped me understand and verify my tests. ChatGPT suggested testing guesses both above and below the secret number to confirm the hint messages were correct. It also suggested testing the New Game button after winning to make sure the game state was fully reset. These tests helped me confirm that my fixes worked as intended

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
