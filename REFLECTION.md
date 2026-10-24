# Reflection

## Who did what
We wrote the code together, during the same working sessions. Everyone took part in writing and testing next_day and after_days, and we all discussed the answers to the Think and Extra questions.
- Alpha Oumar Diallo
- Joel Bocovo
- Guemsu Badje Grace Sonia
- Pape Moussa Diouf
- Awa Thioub


## One bug we had
The problems I encountered:

 While modifying next_day, we made an indentation mistake: return new was placed at the level of the for i loop instead of after the for j loop, so it ended up inside the loop over j. The function therefore returned too early, after computing only the first column. We got the right first value but 0 for the second one, for example [0.8, 0.0] instead of [0.8, 0.2].

## How we fixed it
We compared our output with the expected results in the test cell and noticed that the second value was always 0. This told us that the function was returning before the loop over j had finished. We moved return new to the same level as for j, after both loops, and all the results then matched the expected ones.

## Other difficulties and what we learned
1.	Understanding and writing the distribution formula. At first, the formula given by the lecturer was hard to understand, and our first attempts at writing next_day failed. Once we understood that tomorrow's distribution is obtained by combining today's distribution with the columns of the matrix, we rewrote the function to match the lecturer's expression.

	2.	Results that did not sum to 1. Some of our initial results did not match the expected [0.72, 0.28], and their sum was not equal to 1. The cause was that the code for tasks 1 and 2 and the code for tasks 3 and 4 were mixed in the same cells. Separating them gave correct results.
   
	3.	Many digits after the decimal point. We also got results such as [0.7200000000000002, 0.28] and first thought the formula was wrong. After some research, we learned that computers cannot store most decimal numbers exactly, so a tiny error remains. The formula was correct, and we used round() to two decimal places to display the expected result.
    
	4.	Validating the matrix. Since the user should be free to provide their own matrix P, we wrote a function that checks that P is non-empty and square, and that each distribution sums to 1 (within a tolerance TOLERANCE = 1e-9). This ensures that a forecast can be made.
    
	5.	Why the distribution stops changing. It was hard to see why the distribution becomes stable after many days. Every day, the matrix mixes the distribution a little more, so after a few days the weather of the first day is forgotten. The distribution converges to a value that depends only on the matrix, not on the starting point.
    
	6.	The Extra part: a case without convergence. With the given matrix, if it is sunny today it rains tomorrow for sure (100%), and if it rains today it is sunny tomorrow for sure (100%). The weather must change every day, so it is a 2-day cycle. There is no mixing, so the start is never forgotten and the numbers never stop changing. This is the opposite of point 5.
