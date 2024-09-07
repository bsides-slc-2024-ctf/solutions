# Climber BSides Cache 2024
---

## Introduction

In this challenge, we were simply provided with an elf binary (linux executable) to reverse.

After downloading the binary and adding execute permissions with chmod +x, running the binary results in three questions, prompting the user for an answer:
1. Enter the mountain height (feet):
2. Enter the type of climb (ice, rock, mixed):
3. We lost this input in the mountains... We don't remember what it asks for:

Inputing random answers results in the message: "Checks failed. Are you prepared for this ascent?"

So then, it's time to spin up Ghidra.

---

## Reversing

Opening the file in Ghidra and runing the default auto-analysis identifies the main function, which is always a good place to start. (fig. 1)

In the main function there are three print statements, one for each of the questions we saw during execution. Underneath each of the print statements is a corresponding scanf statement, which takes in the user input. (fig. 2)

Once the answers are collected there is an if statement, which checks whether the input value is greater than 14000, giving us the answer to the first question. (fig. 3)

If the first statement is true it will continue to check if the input from the second value is equal to the string "rock", which matches with one of the provided options seen in the second question, once again giving us our answer.

Lastly, if the previous statement is true, the value of the input for the final and seemingly unanswerable question is simply checked against the number 2.

There is a final function which runs if all questions are answered correctly. This function simply calls another function, passing in an argument. This final function appears to calculate and return the flag. However seeing as we have all the answers, there is no need to reverse the flag calculation.

With the answers noted down, we can run the executable and get the flag.
1. 14001
2. rock
3. 2

---

# Writeup by Fr3ki
[github](https://github.com/Fr3ki)  [x](x.com/Fr3ki_)  [blog](https://frk3i.xyz)
