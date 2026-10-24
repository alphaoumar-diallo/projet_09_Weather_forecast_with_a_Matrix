# Reflection

## Who did what
We wrote the code together as a group, during the same working sessions.
Everyone took part in writing and testing `next_day` and `after_days`,
and we all discussed the answers to the Think and Extra questions.
- Alpha Oumar Diallo
- Joel Bocovo
- Guemsu Badje Grace Sonia
- Pape Moussa Diouf
- Awa Thioub


## One bug we had
The problems I encountered:

 1. I had difficulty figuring out how to write the function that determines tomorrow's distribution based on today's distribution. After several unsuccessful attempts, I adjusted my function to match the expression provided by the lecturer. 

2. Two of my initial results did not match [0.72, 0.28] instead, they were [0.220000000000000, 0.28] which was incorrect, as the sum did not equal 1. To fix this, I simply separated the code for tasks 1 and 2 from the code for tasks 3 and 4; the results are now correct. 

3. I assumed that the user should have the freedom to provide the matrix P themselves, so I wanted to create a function that verifies that P is a non-empty, square matrix and that the sum of each distribution equals 1 (within a tolerance of TOLERANCE=1e-9), ensuring that a forecast can be made.

4. At first, it was hard for me to understand the distribution formula that the teacher gave us. But after some time, I understood it.

5. Then, I was confused by this result with many digits after the decimal point: [0.7200000000000002, 0.28]
I thought the formula was wrong. But after some research, I found that the formula was correct. The computer cannot store decimal numbers exactly, so it keeps a very small error. To get the expected result, I used the round() function to round the numbers to two decimal places.

6. Also, it was hard for me to understand why the distribution stops changing after many days. In the end, I understood that every day, the matrix mixes the distribution a little. After a few days, the weather of the first day is forgotten. The distribution becomes stable at a value that depends only on the matrix, not on the start.

7. For the Extra part of the project, with the given matrix, if it is sunny today, it rains tomorrow for sure (100%). If it rains today, it is sunny tomorrow for sure (100%). The weather must change every day: it is a 2-day cycle. There is no mixing, so the start is never forgotten and the numbers never stop changing.

8. While we were modifying `next_day`, I made an
indentation mistake: I put `return new` at the level of the `for i` loop
instead of the `for j` loop, so it was inside the loop over `j`.

9. The function returned too early, after computing only the first column.
We got the right first value but 0 for the second one, for example
`[0.8, 0.0]` instead of `[0.8, 0.2]`.

## How we fixed it
We compared our output with the expected results in the test cell and saw
that the second value was always 0. We understood that the function was
returning before the loop over `j` was finished. I moved `return new` to
the same level as `for j`, after both loops, and then all the results
matched the expected ones.
