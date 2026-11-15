# Lab 05 — Conclusion

<!--
Read this before you write.

This file is graded by your instructor, by hand, and it is worth 6 of the 15 points.

- Type it yourself. Do not use a chatbot, an AI assistant, an AI autocomplete or a "rewrite my
  text" tool for any part of it, not even for grammar. English that is plain and a little
  clumsy but yours is better than polished text that is not.
- Use your own numbers. Every number you quote must be one your own notebook printed. Copy
  the number exactly as it appeared. A number your notebook did not print is marked as wrong.
- Answer in your own words, about 80-200 words per question. A short answer that uses your
  numbers beats a long answer that could have been written by anyone.
- Delete these comment lines if you like. Keep the three headings and the last line.
-->

## 1. Which layer changed your results the most?

Give the numbers before -> after for that layer (correct / wrong / no answer, out of 20) and say
whether it changed what the agent *can do* or only what it *admits*. If no layer changed the
number of correct answers, say so and explain what the layers did change instead.

Player one changed the results the most the of correct answers went from 16 out 24 to 18 out of 24, while wrong answers went from 4 to 6 and no answers went from 4 to 0. So before 16/4/4 and after is 18/6/0. This changed what the agent *can do* because instead of crashing on tool error it read the error message and fixed region names that were alternative, for example, 'Karagandy' and 'the city of Almaty' and the layer 2(18/6/0) changed nothing and the layer 3(18/4/2) only changed what the agent *admits* and it changed not supported wrong answers to unverified.

## 2. One failure the full harness did not fix

Pick one question that the full harness (layer 3) still gets wrong or refuses. Give its id
(q01 ... q20). Open its trace in the notebook: at which step did it go wrong, and what did
the model do instead? Name one thing you would add to the harness, and what it would cost
(extra model calls, tokens, time, or a new way to fail).

The full harness still failed q18 which asked for the percentage point change CPI in Jumbyl between 2022 and 2025. In the trace the model first got 16.1% and 10.6% then it went wrong with step 2 and calculated With 16.1 - 10.6 / 100 which gave 0.055 and it answered 0.55 percentage point instead of 5.5 and It gave 'unverified' after layer 3 sent that back.
I would add percentage point subtraction tool or maybe something for checking with formula so it does not makes a mistake with dividing by 100 but this would extra tokens every time it runs.

## 3. Workflow or agent for the monthly ranking?

Dala Insight wants to publish, every month, "which region is highest and which is lowest on one
indicator in one year". Would you ship the fixed workflow or the agent? Use the accuracy, the
number of model calls, the tokens and the time you measured in Part 1. Then say in one sentence
what kind of question would make you choose the other one.

I would ship the fixed workflow. so in part 1 on the 15 fixed shape questions the workflow achieved better accuracy(13/15 vs 9/15) and it used fewer model calls(15 vs 26) and its use of tokens were 5 times less(3852 vs 19835). It showed that it three times faster too(16.4 vs 50.2)
I would choose the agent instead for open-ended questions that need several steps or maybe for looking up unfamiliar regions aliases first.

---

I wrote this file myself, without any AI tool.
