# Midterm 1: answers

GitHub username: Altynai06n1
Session code: KETTLE-62
Fingerprint: d90a5e15

> Fill in the three lines above from `my_data/DATA.md`. Do not rename headings or table columns: a script reads the numbers.
> Write only in the empty cells and lines. Percentages as 0.78 or 78 %, money as plain numbers.

## AI-use declaration

I used Claude to write the code (partially). I wrote the conclusions and texts fully by myself.

## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|---|---|---|---|
| A | 0.4833 | 0.6000 | 0.6833 | 0.5593 |
| B | 0.4667 | 0.6333 | 0.8667 | 0.5976 |

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 | 0.6000 | 0.4737 | 0.7143 |
| A, k=5 | 0.6833 | 0.5577 | 0.7869 |
| B, k=3 | 0.6333 | 0.5068 | 0.7438 |
| B, k=5 | 0.8667 | 0.7583 | 0.9309 |

### 1c. Annual model cost in USD

| candidate | annual cost |
|---|---|
| A, k=3 | 23043.04 |
| A, k=5 | 30624.00 |
| B, k=3 | 14931.56 |
| B, k=5 | 17104.86 | 

### 1d. Decision (at most 150 words)

Chosen candidate: B, k=5
I choose (B, 5). (A, 5) costs $30,624 per year. The budget is $26,800, so I cannot choose it. 
Of the three options I can afford, (B, 5) finds the right chunk most often: 0.867 (interval 0.76 to 0.93). 
Its interval does not overlap with (B, 3) (0.63, interval 0.51 to 0.74) or with (A, 3) (0.60, interval 0.47 to 0.71). 
So the data show that (B, 5) is better than both. (B, 5) is also cheaper than (A, 3): $17,105 per year against $23,043. 
Recall of (B, 5) by language: EN 0.80, RU 0.90, KK 0.90. English is the worst. 
But we have only 20 questions per language, so the intervals overlap (EN: 0.58 to 0.92). A gap between the languages is not proven.

### 1e. Next measurement (at most 60 words)

We should add at least 200 more test questions per language, then measure the recall of (B, 5) for each language again. 
Now the English interval is wide (0.58 to 0.92). 
More questions would show if English is really worse. If it is, we could try a different chunk size for English.

## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H | 0.928 | RU, degraded | 0.867 | 0.703 | 0.947 | 39989.40 |
| L | 0.783 | RU, clean | 0.700 | 0.521 | 0.833 | 7200 |

Personal-data pages per year sent abroad under H: 341275

### 2b. Memo (at most 300 words)

Recommendation
I recommend choosing pipeline L. It is cheaper and keeps personal data on a server in Kazakhstan. 
But people should check documents when the AI is not sure.

H works worst on damaged Russian scans, with 86.7% accuracy (95% interval: 70.3–94.7%). 
L works worst on clear Russian scans, with 70.0% accuracy (52.1–83.3%). 
These results are not enough to say which system is worse for these groups because the intervals overlap.
Overall, H has 92.8% accuracy, while L has 78.3%. 
Their intervals do not overlap, so H is more accurate overall. 
Each group has only 30 invoices, so the results for each group may not be fully reliable.

Personal Data. About 17% of pages contain a person's name and ИИН. With H, 341,275 pages with personal data per year would be sent outside Kazakhstan. Law No. 94-V covers the ИИН.
H uses a data centre abroad, and the vendor stores the scans. We do not know how long the scans are kept. L uses our own server in Kazakhstan, and the bank decides how long to keep the scans. Before choosing H, we must check if sending personal data abroad is allowed by law.

Safeguards: deleting scan images every month; review the access log, people check uncertain pages, and each month we test 100 pages to measure the error rate.

Final Decision
L costs $7,200 per year, while H costs $39,989. L is cheaper and keeps personal data in Kazakhstan. 
Its main problem is lower accuracy, so some invoices may contain errors. 
If checking documents becomes too expensive, we can consider H again after checking the legal risks.

## Part 3: Explain your own numbers

### Q1

Number: 2.62
Why (at most 40 words): The Kazakh input is 2.84 times longer, but the output only 2.0 times. 
Output costs 5 times more per token, so its small growth matters a lot. 
So the bill ratio (2.62) is lower than the token ratio (2.79).

### Q2

Number: 2.7
Why (at most 40 words): Only the English chunk is too long: 526 e5 tokens, but the limit is 512. 
Russian (256) and Kazakh (152) fit. The extra end of the chunk is not used for search, and there is no error message.

### Q3

Number: 66.7
Why (at most 40 words): Top-p keeps the most likely tokens (here 3, together 0.917) and drops the rare ones. 
Temperature changes all probabilities but drops no token, so every token can still be chosen.

### Q4

Number: 8
Why (at most 40 words): The leaderboard prefers X (73 against 67), because "I don't know" gives 0 points, so guessing pays off. 
With the penalty, Y wins (27 against 19). So a model should learn to say "I don't know" when unsure.

### Q5

Number: 12915
Why (at most 40 words): The first message is paid for 14 times, once in every turn. 
Prompt caching makes the repeated start of the prompt cheaper, but the history still gets longer and longer.
