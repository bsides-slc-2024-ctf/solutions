# Climber BSides Cache 2024
---

In this challenge, we were simply provided with an elf binary (linux executable) to reverse.

After downloading the binary and adding execute permissions with chmod +x, running the binary results in three questions, prompting the user for an answer:
1. Enter the mountain height (feet):
2. Enter the type of climb (ice, rock, mixed):
3. We lost this input in the mountains... We don't remember what it asks for:

Putting in guesses results in the message: "Checks failed. Are you prepared for this ascent?"

So then, it's time to start up Ghidra.

---

Opening the file in ghidra, and runing it's default analysis identifies the main function, which is always a good place to start. (fig. 1)

In the main function, we can see the three print statements and their respective inputs.

Later in the function, we see a check, if the input from the first question is greater than 1400, we continue, else we automatically fail. Giving us the answer to the first question.

Next the input from the second question is checked against the string "rock", giving us our answer to the second question.

Lastly we see the input from the last question being compared against the integer 2.

There are some functions that run if all the answers were correct, which compute and return the key, however now that we have the answers, there is no need to reverse engineer those functions.

Running the executable and inputing the correct options gives us the flag:
1. 14001
2. rock
3. 2

Writeup by Fr3ki
