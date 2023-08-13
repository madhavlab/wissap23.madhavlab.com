---
layout: page
title: "01: Music Search: Query by Humming"
permalink: /wissap-cup/qbh
---

## Overview

Finding the same or similar audio in a massive audio corpus is computationally and memory expensive. 
Audio fingerprinting is a technique to index audio datasets for efficient retrieval. Retrieval entails matching the database entries with a given query audio. 
 <!-- that derives a content-based audio summary and links it with similar audio fragments in the database. It allows for an efficient and quick search against other audio fragments. -->
The task in this challenge is to develop method to index a large audio database and search a given audio query efficiently. The query could be a noisy and distorted segment from one of the audios in the database.

**Task**: Given a monophonic query $$q$$, we wish to return top-5 similar matches in the search database D. The song-id of the query is determined as the song-id of the most similar sequence in search database D.

## Guidelines

- Neural network size to be restricted to be no more than 3M.
- Submission via Kaggle must be in a .csv format with first column representing the 'query_filename' and column 2 through column 6 representing song-id of the top-5 most similar matches in the search database. 
- Each team can submit for a maximum of 3 times per day, until the release of the test set, after which the latest submission shall be considered as the team’s final submission. 
- The initial leader board will be based on the MRR score of the model based on the .csv submission. 
- The criteria for evaluation will be: 
    - Time: The model must find the best matches for all the query files in the test set within a stipulated amount of time. The accuracy metric will not be checked unless the model is able to find the best matches within the given time limit 
    - Accuracy: Next the models MRR score will be checked on the test set. The teams with higher MRR score on this test set will be ranked higher that the teams with lower MRR score. 
- Mean Reciprocal Rank or MRR measures how far down the ranking the first relevant document is. If MRR is close to 1, it means relevant results are close to the top of search results - what we want! Lower MRRs indicate poorer search quality, with the right answer farther down in the search results.

## Submission

- Upon registering your team for the challenge via the form on the [WiSSAP Cup](/wissap-cup) page, you will recieve a Kaggle invitation to join the competition.
- Instructions on how to submit shall be shared via a video tutorial before the submission begins.
- The latest submission before the release of the test set (20th October) shall be considered as the team's final submission.

## FAQ

We will fill this section with questions we receive and our answers.

For additional information, you can reach us via email at [{{ site.email }}](mailto:{{ site.email }})

---