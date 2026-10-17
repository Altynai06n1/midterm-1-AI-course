# Midterm 1: answers

GitHub username:
Session code:
Fingerprint:

> Fill in the three lines above from `my_data/DATA.md`. Do not rename headings or table columns: a script reads the numbers.
> Write only in the empty cells and lines. Percentages as 0.78 or 78 %, money as plain numbers.

## AI-use declaration

I used Claude to write the code (partially). I wrote the conclusions and texts fully by myself.

## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

config | recall@1 | recall@3 | recall@5 | MRR@10
A | 0.4333 | 0.7333 | 0.8500 | 0.5910
B | 0.1833 | 0.3667 | 0.6500 | 0.3406

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

Budget: $17,600
candidate | hits | recall@k | lower | upper 
A, k=3 | 44/60 | 0.7333 | 0.6099 | 0.8287 
A, k=5 | 51/60 | 0.8500 | 0.7389 | 0.9190 
B, k=3 | 22/60 | 0.3667 | 0.2562 | 0.4932 
B, k=5 | 39/60 | 0.6500 | 0.5236 | 0.7583 

### 1c. Annual model cost in USD

candidate | annual cost 
A, k=3 | 15,069.01 
A, k=5 | 20,155.65 
B, k=3 | 9,434.08 
B, k=5 | 10,764.11 

### 1d. Decision (at most 150 words)

Chosen candidate: B, k=5

I choose (B, 5). 
(A, 5) finds the right chunk most often (0.85), but it costs $20,156 per year. The budget is $17,600, so I cannot choose it.

Of the options I can afford, (A, 3) is the best (0.733, interval 0.61 to 0.83). 
But the interval of (B, 5) (0.650, interval 0.52 to 0.76) overlaps with it. 
So the data do not prove that (A, 3) is better.

(B, 5) is cheaper: $10,764 per year, against $15,069 for (A, 3).
Recall of (B, 5) by language: EN 0.65, RU 0.60, KK 0.70. 
Russian is the worst, but we have only 20 questions per language, so the gap is not proven.
I reject (B, 3): its recall is only 0.37, and 0.20 for English.

### 1e. Next measurement (at most 60 words)



## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H | | | | | | |
| L | | | | | | |

Personal-data pages per year sent abroad under H:

### 2b. Memo (at most 300 words)

## Part 3: Explain your own numbers

### Q1

Number:
Why (at most 40 words):

### Q2

Number:
Why (at most 40 words):

### Q3

Number:
Why (at most 40 words):

### Q4

Number:
Why (at most 40 words):

### Q5

Number:
Why (at most 40 words):
