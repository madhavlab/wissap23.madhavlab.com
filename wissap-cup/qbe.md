---
layout: page
title: "02: Music Search: Query by Example"
permalink: /wissap-cup/qbe
---

Welcome to the Audio Fingerprinting Competition! 
Audio fingerprinting is crucial in various applications, such as music identification, content recognition, and copyright enforcement. In this competition, participants will have the opportunity to showcase their expertise in developing innovative algorithms for audio fingerprinting, contributing to the advancement of audio technology.
The goal is to develop accurate and efficient algorithms for audio fingerprinting. Participants' systems must accurately match a query audio clip to the corresponding audio track in a database. This task simulates real-world scenarios where audio queries are possibly distorted by noise and reverberation, and the content needs to be quickly and accurately identified. 

**Task**: Participants must create a system capable of identifying the top five matching audio tracks from a reference database. These matches should correspond to a provided monophonic audio query.

**Background**:
Audio fingerprinting systems mainly consist of two components: 
- Representation Learning: This involves the generation of robust and compact representations, a.k.a. audio fingerprints corresponding to distinct audio segments.
- Retrieval:  Involves indexing audio fingerprints derived from the reference audio database. This involves a mechanism for efficiently searching for the best match corresponding to a provided audio query. 

<!-- - For a better picture, refer to the figure below. -->

## Database Description

The competition database consists of diverse audio tracks spanning various genres. The database is divided into two main parts: 

- <u>Development database</u>: Participants will have access to a database containing 8000 audio tracks (*.wav). These tracks are sampled at a rate of 48kHz and each audio clip spans 30 seconds. Alongside the audio tracks, users will also be provided with a collection of noise clips and Room Impulse Responses (RIRs) to facilitate the creation of their representation learning models. Users may split this database into subsets for training and validation purposes. Furthermore, the same database can be employed to assess the performance of retrieval techniques.

- <u>Test database</u>: It consists of reference audio tracks (relatively larger) and query audio clips. The reference audio tracks form the basis for generating fingerprints, while the query audio clips are used to evaluate the matching performance of the participants' systems. The query clips are 2 seconds long and intentionally distorted by adding noise and reverberation at different SNR(dB) levels.


## Evaluation

- The system will be tested using 100 distorted audio clips (*.wav), each lasting 2 seconds. These clips are deliberately distorted through the addition of noise and reverberation, spanning various distortion levels. The noise may vary from 0dB to 20dB SNR, while the added reverberation ranges from 0.1s to 0.7s [t60 level](https://en.wikipedia.org/wiki/Reverberation/).
- The system's performance will be evaluated based on its <a href="https://en.wikipedia.org/wiki/Mean_reciprocal_rank" target="_blank">Mean Reciprocal Rank (MRR)</a>, reflecting its robustness and the retrieval time **t**, which indicates search efficiency. It is essential to note that participants are discouraged from employing brute-force search methodologies to identify the best matches. The final rankings will be determined by a combination of accuracy and speed, with an emphasis on achieving a balance between the two.

<!-- - For all 100 chunks from the test set, the returned top-5 `file_ids` in order of the confidence for each shall be matched with the ground truth file_id. The final score will be the mean of the MRR score computed for all such query files.
- The final score for evaluation will be computed as- -->

<div align="center">
<img class="width-score width-max-100px" src="{{ "./images/score_qbe.png" | relative_url }}">
</div>

## Submission

- Upon registering your team for the challenge via the form on the [WiSSAP Cup](/wissap-cup) page, you will recieve a Kaggle invitation to join the competition.
- Submission via Kaggle must be in a `.csv format` with first column representing the `query_filename` and column 2 through column 6 representing `song_id ` of the top-5 similar matches in the reference database. 
- Each team can submit for a maximum of 3 times per day, until the release of the test set, after which the latest submission shall be considered as the team’s final submission. 
<!-- - The aim should be to achieve robust embeddings given an audio chunk, such that it is insensitive to noise and distortions. For generalization, the training set also consists of some noisy and distorted audio recordings. -->
- Once the test set is released, participants are required to submit their algorithms and models along with comprehensive documentation outlining the technical details of their approach. Submissions should include:
    - A detailed explanation of the fingerprinting algorithm.
    - The notebook on Kaggle with their system. The developed QBE system should inputs raw audio clip (query, sampled at 16kHz) and output the top-5 identified audio tracks. The Kaggle leaderboard on the test set shall be the final ranking of each participating team.
- Detailed instructions on how to submit shall be shared via a video tutorial soon.

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