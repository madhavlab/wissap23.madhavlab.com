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

**Task**: Given a monophonic humming query $$q$$, we wish to retrieve top-5 similar matches in the search database D. The song-id of the query is determined as the song-id of the most similar sequence in search database D. 
ground truth  MIDI or wav file from user’s humming or singing.  

## Guidelines

- The participating teams are required to train a model such that it is able to retrieve top-5 matches in a search database.
<!-- - The training set is the MIR-QBSH (https://www.music-ir.org/mirex/wiki/2020:Query_by_Singing/Humming) that consists of ~4K humming queries of nearly ~10s each corresponding to database of 48 MIDI files. The teams are required to convert the MIDI files to the audio files. The test set consists of ~4000 query files each corresponding to database of 150 + songs.  -->
- The aim is to build a robust model such that it is insensitive to the noisy and distorted queries. 
- **Queries**: Human Singing/ humming audio snippets  
- **Database**:  Ground truth MIDI files and wav files of studio recordings
- **Challenges**: Note, the MIDI files are monophonic, while the wav files may be polyphonic. This makes the search very difficult. In addition, the queries are imitations of the original song. Hence, they can have variation in pitch and tempo.
- **Training Dataset**:   The participating teams may use MIR-QbSH, IOACAS-QbH, MIR-1K, fma-small dataset for training their models.
- MIR-QbSH dataset is a classic QbH dataset with 4800 queries and 48 ground truth MIDI. All queries are from the beginning of references. IOACAS-QbH dataset has 759 queries and 298 monophonic ground-truth MIDI files. Unlike MIR-QbSH, the queries may not be at the beginning of references. The participants may use MIR-QbSH or IOACAS-QBH or a combination of two evaluate their models search performance during training.
- MIR-1K and fma-small consists of studio recordings of 1000 and 8000 songs respectively. The participants may use these two datasets to train their models to learn strong representations. The queries in MIR-QbSH and IOACAS-QbH datasets can be used to adapt their models to the different pitch and tempo variations a humming query may contain, as it is only an imitation of the original song.  
- The links to the datasets are as follows
    - [MIR-QbSH](https://music-ir.org/evaluation/MIREX/data/qbsh/MIR-QBSH-corpus.tar.gz)
    - [IOACAS-QbH](https://music-ir.org/evaluation/MIREX/data/qbsh/IOACAS_QBH_Corpus.tar.gz)
    - [MIR-1K](http://mirlab.org/dataset/public/MIR-1K.zip)
    - [fma-small](https://os.unil.cloud.switch.ch/fma/fma_small.zip)


### Evaluation

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
- Detailed instructions on how to submit shall be shared via a video tutorial soon.

## References

- [Query by humming of midi and audio using locality sensitive hashing](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=4518093)
- [Query by Humming by Using Locality Sensitive Hashing Based on Combination of Pitch and Note](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6266272)
- [A Note Based Query By Humming System using Convolutional Neural Network](https://www.isca-speech.org/archive_v0/Interspeech_2017/pdfs/1590.PDF)

## FAQ

We will fill this section with questions we receive and our answers.

For additional information, you can reach us via email at [{{ site.email }}](mailto:{{ site.email }})

---