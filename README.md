# Essay-Scoring -- DebertaV3 vs. ChatGPT

## Background and Motivation
This work is based on a Kaggle competition to develop a method to automatically score essays written by English language learners in 8th through 12th grade. Using AI models for automated scoring would help increase feedback for students and provide support for teachers.

https://www.kaggle.com/competitions/feedback-prize-english-language-learning 

Essay scoring consisted of 6 categories: cohesion, convention, grammar, phraseology, syntax and vocabulary
Each category is scored from 1 to 5 on 0.5 level increments.

In this study two main approaches were compared:

* Fine-Tuning: A small, pre-trained model of 86M parameters (DebertaV3) was fine-tuned to evaluate the essays.
* Prompt Engineering: Using both ChatGPT 3.5 and 4 the model was prompted to score the given essays.

## Data

3911 essays were split into 80% Train, 10% Validation and 10% Test datasets.

The overall distribution of average scores were centered around a mean of 3.1 . Based on the distribution a very significant class imbalance exists with most of the scores centered around the mean.

<img width="394" alt="Screenshot 2024-01-12 at 5 03 23 PM" src="https://github.com/kdevoe/Essay-Scoring/assets/31428365/fbd0c429-96c0-4ad8-b98f-90d59001ee6f">  
       
One potential concern with using DebertaV3-base for fine-tuning was a max input token length of 768. This means approximately 10% of essays are be truncated during training. Comparing the populations of scores for essays above and below this limit the average increases from 3.1 for not truncated to 3.3 for truncated. Although small a t-test shows this change to be significant and a model with a larger input window should be evaluated for future work.

<img width="393" alt="Screenshot 2024-01-12 at 5 11 49 PM" src="https://github.com/kdevoe/Essay-Scoring/assets/31428365/eed32862-1c30-4e0c-97d4-9949a5d04672">


## Fine-Tuning

:warning: Work in Progress as of 1/10/2024 :hammer:
