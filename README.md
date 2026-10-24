# Project 09: Weather Forecast with a Matrix

## What the program does
The program predicts the weather using a transition matrix (a Markov chain).
Each row of the matrix gives the probabilities of tomorrow's weather,
knowing today's weather.

- `next_day(dist, P)`: computes tomorrow's distribution from today's.
  For each state j, it adds `dist[i] * P[i][j]` over all states i.
- `after_days(start, P, days)`: repeats `next_day` several times to get
  the distribution after a given number of days.

Results are rounded (10 decimals in the functions, 4 decimals when displayed)
to hide floating-point errors: for example `0.7200000000000002` is shown as `0.72`.

## How to run
1. Open `Project_09_Weather_Forecast_with_a_Matrix.ipynb` in Google Colab.
2. Run the cells in order, from top to bottom.

## Example results
With P = [[0.8, 0.2], [0.4, 0.6]] (states: Sunny, Rainy):

- `next_day([1, 0], P)` gives `[0.8, 0.2]`
- `after_days([1, 0], P, 2)` gives `[0.72, 0.28]`
- `after_days([1, 0], P, 50)` gives about `[0.6667, 0.3333]`

With P3 (states: Sunny, Cloudy, Rainy) starting from `[1, 0, 0]`:

P3 = [[0.7, 0.2, 0.1],
      [0.3, 0.4, 0.3],
      [0.2, 0.3, 0.5]]

| Days | Sunny  | Cloudy | Rainy  |
|------|--------|--------|--------|
| 1    | 0.7    | 0.2    | 0.1    |
| 2    | 0.57   | 0.25   | 0.18   |
| 5    | 0.4685 | 0.2794 | 0.2521 |
| 10   | 0.4568 | 0.2825 | 0.2607 |
| 50   | 0.4565 | 0.2826 | 0.2609 |

In the long run, about 26% of the days are rainy.

## Think and explain
With the starting distributions `[1, 0, 0]`, `[0, 0, 1]` and `[1/3, 1/3, 1/3]`,
the distribution after 50 days is the same: about `[0.4565, 0.2826, 0.2609]`.
Each day, the matrix mixes the distribution a little more, so the starting
day is forgotten. Only the matrix decides the long-run result.

## Extra
With `[[0, 1], [1, 0]]` and `start = [1, 0]`, the first 6 days are
`[0, 1]`, `[1, 0]`, `[0, 1]`, `[1, 0]`, `[0, 1]`, `[1, 0]`.
It never settles: Sunny always becomes Rainy and Rainy always becomes Sunny,
so it is a 2-day cycle. There is no randomness to mix the states,
so the starting point is never forgotten.
