---
layout: page
title: "02: Music Search: Query by Example"
permalink: /wissap-cup/qbe
---

Finding the same or similar audio in a massive audio corpus is computationally and memory expensive. 
Audio fingerprinting is a technique to index audio datasets for efficient retrieval. Retrieval entails matching the database entries with a given query audio. 
The task in this challenge is to develop method to index a large audio database and search a given audio query efficiently. The query could be a noisy and distorted segment from one of the audios in the database.

The goal is to develop accurate and efficient algorithms for audio fingerprinting. Participants' systems must accurately match a query audio clip to the corresponding audio track in a database. This task simulates real-world scenarios where audio queries are possibly distorted by noise and reverberation, and the content needs to be quickly and accurately identified. 

**Task**: Given a monophonic query q, the goal is to search for the top 5 similar matches in the reference database. The song-id of the query is identified as the `song_id` of the best match retrieved from the database.

**Background**:
Audio fingerprinting systems mainly consist of two components: 
- Representation Learning: This involves the generation of robust and compact representations, a.k.a. audio fingerprints corresponding to distinct audio segments.
- Retrieval:  Involves indexing audio fingerprints derived from the reference audio database. This involves a mechanism for efficiently searching for the best match corresponding to a provided audio query. 

## Guidelines

- The participating teams are required to train a model such that it is able to search for the **top- 5 matches** in a reference database.
- An audio chunk from nearly 100 randomly chosen files from the test set shall be fed into the system, which is expected to return the `file_ids` of the top-5 matched files in the test set.
- The aim should be to achieve robust embeddings given an audio chunk, such that it is insensitive to noise and distortions. For generalization, the training set also consists of some noisy and distorted audio recordings.
<!-- - For a better picture, refer to the figure below. -->

#### Database Description

The competition database consists of diverse audio tracks spanning various genres. The database is divided into two main parts: 

- <u>Development database</u>: Participants will have access to a database containing 8000 audio tracks. These tracks are sampled at a rate of 48kHz and each audio clip spans 30 seconds. Alongside the audio tracks, users will also be provided with a collection of noise clips and Room Impulse Responses (RIRs) to facilitate the creation of their representation learning models. Users may split this database into subsets for training and validation purposes. Furthermore, the same database can be employed to assess the performance of retrieval techniques.

- <u>Test database</u>: It consists of reference audio tracks (relatively larger) and query audio clips. The reference audio tracks form the basis for generating fingerprints, while the query audio clips are used to evaluate the matching performance of the participants' systems. The query clips are 2 seconds long and intentionally distorted by adding noise and reverberation at different SNR(dB) levels.


#### Evaluation

- Each submission shall be evaulated based on the <a href="https://en.wikipedia.org/wiki/Mean_reciprocal_rank" target="_blank">Mean Reciprocal Rank (MRR)</a> and the consumed time on the test set.
- MRR measures how far down the ranking the first relevant document is. If MRR is close to 1, it means relevant results are close to the top of search results - what we want! Lower MRRs indicate poorer search quality, with the right answer farther down in the search results.
- For all 100 chunks from the test set, the returned top-5 `file_ids` in order of the confidence for each shall be matched with the ground truth file_id. The final score will be the mean of the MRR score computed for all such query files.
- The final score for evaluation will be computed as-

<div align="center">
<img class="width-score width-max-100px" src="{{ "./images/score_qbe.png" | relative_url }}">
</div>

## Submission

- Upon registering your team for the challenge via the form on the [WiSSAP Cup](/wissap-cup) page, you will recieve a Kaggle invitation to join the competition.
- Submission via Kaggle must be in a `.csv format` with first column representing the `query_filename` and column 2 through column 6 representing `song_id ` of the top-5 most similar matches in the reference database. 
- Each team can submit for a maximum of 3 times per day, until the release of the test set, after which the latest submission shall be considered as the team’s final submission. 
- Detailed instructions on how to submit shall be shared via a video tutorial before the submission begins.

## References

- [Simultaneously Learning Robust Audio Embeddings and Balanced Hash Codes for Query-by-Example](https://ieeexplore.ieee.org/abstract/document/10096103)
- [Attention-based Audio Embeddings for Query-by-Example](https://arxiv.org/pdf/2210.08624.pdf)

<!-- 1. model train for rep learning
2. dbs: 
    1. fma_small (8K music files) for training, fma_med (30K music files) for test (building fingerprint database). 
    2. noises and rirs (MUSAN)
3. build search system: input: .wav file output: song id, time offset
4. metric: does a song id match (Recall)? if yes, is the retrieved time offset differernce is within +-0.1s? MRR?? -->

## FAQ

We will fill this section with questions we receive and our answers.

For additional information, you can reach us via email at [{{ site.email }}](mailto:{{ site.email }})

---
---