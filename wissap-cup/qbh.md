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

- The participating teams are required to train a model such that it is able to search for top-5 best matches in search database.
- The training set is the MIR-QBSH (https://www.music-ir.org/mirex/wiki/2020:Query_by_Singing/Humming) that consists of ~4K humming queries of nearly ~10s each corresponding to database of 48 MIDI files. The teams are required to convert the MIDI files to the audio files. The test set consists of ~4000 query files each corresponding to database of 150 + songs. 
- The aim is to build a robust model such that it is insensitive to the noisy and distorted queries. 
- The neural network size is to be restricted to be no more than 3M.

### Evaluation

- Each submission shall be evaluated based on the Mean Reciprocal Rank (MRR) on the test set.
- MRR measures how far down the ranking of the first relevant song is. It is calculated as 1/r where r is the ranking of the first relevant song. If MRR is close to 1, it means relevant results are close to the top of search results (what we want!).  Lower MRRs indicate poor search quality, with the right answer being further down in the search results. 

## Submission

- Upon registering your team for the challenge via the form on the [WiSSAP Cup](/wissap-cup) page, you will recieve a Kaggle invitation to join the competition.
- Submission via Kaggle must be in a `.csv format` with first column representing the `query_filename` and column 2 through column 6 representing `song_id ` of the top-5 most similar matches in the reference database. 
- Each team can submit for a maximum of 3 times per day, until the release of the test set, after which the latest submission shall be considered as the team’s final submission. 
- Detailed instructions on how to submit shall be shared via a video tutorial before the submission begins.

## FAQ

We will fill this section with questions we receive and our answers.

For additional information, you can reach us via email at [{{ site.email }}](mailto:{{ site.email }})

---