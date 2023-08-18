---
layout: page
title: "02: Music Search: Query by Example"
permalink: /wissap-cup/qbe
---

Finding the same or similar audio in a massive audio corpus is computationally and memory expensive. 
Audio fingerprinting is a technique to index audio datasets for efficient retrieval. Retrieval entails matching the database entries with a given query audio. 
The task in this challenge is to develop method to index a large audio database and search a given audio query efficiently. The query could be a noisy and distorted segment from one of the audios in the database.

**Task**: Given a monophonic query q, the goal is to search for the top 5 similar matches in the reference database. The song-id of the query is identified as the `song_id` of the best match retrieved from the database.


## Guidelines

- The participating teams are required to train a model such that it is able to search for the **top- 5 matches** in a reference database.
- The training set consists of ~8K audio (music) files of nearly 30s each. The test set consists of ~30K audio (music) files. 
- An audio chunk from nearly 100 randomly chosen files from the test set shall be fed into the system, which is expected to return the `file_ids` of the top-5 best matched files in the test set.
- The aim should be to achieve robust embeddings given an audio chunk, such that it is insensitive to noise and distortions. For generalization, the training set also consists of some noisy and distorted audio recordings.
- For a better picture, refer to the figure below.

#### Evaluation

- Each submission shall be evaulated based on the <a href="https://en.wikipedia.org/wiki/Mean_reciprocal_rank" target="_blank">Mean Reciprocal Rank (MRR)</a> on the test set.
- MRR measures how far down the ranking the first relevant document is. If MRR is close to 1, it means relevant results are close to the top of search results - what we want! Lower MRRs indicate poorer search quality, with the right answer farther down in the search results.
- For all 100 chunks from the test set, the returned top-5 `file_ids` in order of the confidence for each shall be matched with the ground truth file_id. The final score will be the mean of the MRR score computed for all such query files.

## Submission

- Upon registering your team for the challenge via the form on the [WiSSAP Cup](/wissap-cup) page, you will recieve a Kaggle invitation to join the competition.
- Submission via Kaggle must be in a `.csv format` with first column representing the `query_filename` and column 2 through column 6 representing `song_id ` of the top-5 most similar matches in the reference database. 
- Each team can submit for a maximum of 3 times per day, until the release of the test set, after which the latest submission shall be considered as the team’s final submission. 
- Detailed instructions on how to submit shall be shared via a video tutorial before the submission begins.


1. model train for rep learning
2. dbs: 
    1. fma_small (8K music files) for training, fma_med (30K music files) for test (building fingerprint database). 
    2. noises and rirs (MUSAN)
3. build search system: input: .wav file output: song id, time offset
4. metric: does a song id match (Recall)? if yes, is the retrieved time offset differernce is within +-0.1s? MRR??

## FAQ

We will fill this section with questions we receive and our answers.

For additional information, you can reach us via email at [{{ site.email }}](mailto:{{ site.email }})

---
---