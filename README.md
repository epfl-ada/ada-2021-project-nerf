# Do US politicians care about climate change?

This team project is a part of the [Applied Data Analysis 2021](https://dlab.epfl.ch/teaching/fall2021/cs401/) curriculum at the EPFL.

The purpose of this file is to explain the project and help you navigate this repo.

## Table of Contents
- [Abstract](#abstract)
- [Goal](#goal)
- [Data](#data)
- [Methods](#methods)
- [Proposed timeline](#proposed-timeline)
- [Organization within the team](#organization-within-the-team)
- [Navigating the repo](#navigating-the-repo)
- [Data story](#data-story)
- [Authors](#authors)

## Abstract
Wildfires, hurricanes, droughts - just another regular year on planet Earth. The common factor is none other than **climate change**.
<br><br>
Climate change is a topic that deeply concerns us all and is potentially the most devastating problem that humanity will have to face so far. Although the impacts of global warming are sporadically occurring, thus providing a false sense of comfort, it is important to address these issues and take action. This is a human responsibility as well as a political one.
<br><br>
For that reason, we want to analyze how concerned are US politicians. Are they raising awareness about global warming and is fighting climate change a part of their agenda? Or perhaps, is this a topic they would rather sweep under the rug?
<br>
Moreover, we want to investigate whether there are any correlations between specific demographical features (e.g. age, education, state of domicile, etc.) or political and business affiliations and the attitude towards climate change.

## Goal
In this project, we aim to analyze quotes from US politicians concerning climate change. This should allow us to paint a picture of the importance of this problem from a politician's point of view.
<br><br>
In addition to this, we strive to provide answers to the following questions:
- How often does a specific politician give statements about climate change? In other words, what is the ratio between climate change and non-climate change quotes?
- Which politician talks the most about climate change?
- Can we relate the opinion about climate change to specific demographic parameters?
- At what points in time do politicians talk (more) about climate change (e.g. during the election periods)?
- What is the emotional atmosphere when speakers talk about climate change?
- Testing how honest and trustworthy are US politicians when they talk about climate change?

Certainly, all the aforementioned questions should be addressed considering given political parties as well.

## Data
The data we will use for our analysis consists of:
- quotes from US politicians published during the period from 2015 to 2020 - acquired from the [Quotebank dataset](https://dlab.epfl.ch/people/west/pub/Vaucher-Spitz-Catasta-West_WSDM-21.pdf)
- additional metadata about the speakers in the Quotebank dataset - acquired from the [Wikidata knowledge base](https://www.wikidata.org/wiki/Wikidata:Main_Page) and available as a `speaker_attributes.parquet` file on [Google Drive](https://drive.google.com/drive/folders/1VAFHacZFh0oxSxilgNByb1nlNsqznUf0). In addition to this `.parquet` file, if some extra (Wiki)data is needed it will be acquired through Wikidata SPARQL queries.

Given that the Quotebank dataset comprises a huge amount of quotes, it is crucial to filter out all those quotes that are not said by US politicians.
<br>
This is feasible by:

- extracting necessary speakers from the `.parquet` file
- merging extracted speakers with the Quotebank dataset

## Methods
In this section, we will give an overview of the processing that needs to be done after preprocessing the data but before the data analysis part. Moreover, we will explain the problem-solving process as well as the feasibility of each task.
<br><br>
Processing that needs to be done:
- extraction of climate change quotes:
    - firstly, training a model using `fasttext` with _unsupervised_ learning
        - generating word embeddings from the model 
        - calculating similarity between the **"climate change"** query vector and the aggregated quotes vectors
        - extraction of most similar quotes based on a threshold <br><br>
    - sedondly, training a `distilled BERT` _supervised_ model for sequence classification
        - getting the probability of a quote being related to climate change
        - taking out quotes with probability higher than certain threshold
- feasibility
    - As a prerequisite for this extraction, we need to ensure that there are enough quotes for training the model. After extracting all the speakers and their quotes that we need for our analysis we gathered an astonishing number of over 5 million quotes - which should be more than enough.
    - In addition to this, there should also be plenty of climate change quotes in order to have sufficient data for further analysis. With a simple regex search for _climate change_, we can see a decent number of quotes. It is only natural to assume that a trained model would provide us with even more and better quotes than a regex search.<br><br>
- sentiment analysis of climate change quotes:
    - determine a sentiment with pretrained `distil BERT model` from **Huggingface**
    - get values between -1 and 1 where negative values represent negative sentiment and vice cersa
    - apply the Sentiment analysis on extracted disaster and climate change-related quotes
    - describe and analyze the values returned to get a better insight into how the model performs
    - use returned values to determine if certain groups of politicians have positive or negative stances towards climate change
    <br><br>
- feasibility
  - To get the most accurate sentiment prediction the input text should be of an adequate form i.e. it should be long enough yet not too long (short sentences are either impactful or do not yield enough information) luckily the extraction process yields enough diversity that we should be able to filter adequate quotes for such an analysis, however we must be careful to not introduce bias into our analysis by doing this.
  - Moreover after manually testing sentiment analysis models we can see that they will be very useful in answering some questions


## Proposed timeline
This project should be completed by December 17th. Our proposed timeline can be found in the table below:

| Period                 | Description               |
| ---------------------- | ------------------------- |
| 13. Nov - 19. Nov      | Extracting quotes about climate change                                               |
| 20. Nov - 27. Nov      | Sentiment and misconception analysis of extracted quotes                                               |
| 28. Nov - 07. Dec      | Data analysis and answering questions                                            |
| 08. Dec - 11. Dec      | Creating data story for a visual representation of the project's findings                 |
| 12. Dec - 17. Dec      | Final revisions           |
| 17. Dec                | Project submission        |

## Organization within the team
Our team consists of four members. We intend to work on every milestone in pairs:
- Pair1 = Edvin + Radenko
- Pair2 = Filip + Natalija.
<br><br>

<table>
<thead>
  <tr>
    <th>Milestones/Pairs</th>
    <th>Pair1</th>
    <th>Pair2</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Extracting climate change quotes</b></td>
    <td>creating the model</td>
    <td>validating the model</td>
  </tr>
  <tr>
    <td><b>Sentiment and misconception analysis</b></td>
    <td colspan="2">
        <ul>produce a model for sentiment analysis (e.g. BERT)
        </ul>
        <ul>afterwards, use CARDS model for claims misinformation prediction</ul>
    </td>
  </tr>
  <tr>
    <td><b>Data analysis</b></td>
    <td>time and political party related analysis</td>
    <td>person-related and demographic factors analysis</td>
  </tr>
  <tr>
    <td><b>Data story<b></td>
    <td colspan="2">
        <ul>each pair will be working on the data story for their own previously completed analysis</ul></td>
  </tr>
  <tr>
    <td><b>Final revisions</b></td>
    <td>revision of Pair2 files</td>
    <td>revision of Pair1 files</td>
  </tr>
</tbody>
</table>

## Navigating the repo
### `preprocessing`
This folder contains all the preprocessing work performed on the input data - both the speakers and quotes are preprocessed.
<br><br>Files:
- [`Wikidata_preprocessing.ipynb`](./preprocessing/Wikidata_preprocessing.ipynb) - handles preprocessing of speakers using Wikidata
    - extracting alive politicians that were affiliated with The Republican or The Democratic party during the period 2015-2020.
- [`Quotebank_preprocessing.ipynb`](./preprocessing/Quotebank_preprocessing.ipynb) - handles preprocessing of quotes from Quotebank
    - extracting quotes that match with the speakers extracted in Wikidata_preprocessing
    - dropping empty or duplicate quotes
### `Main notebooks`
- [`ClimaTextFastText.ipynb`](./ClimaTextFastText.ipynb) - extracting quotes related to climate change using FastText unsupervised model
    - cleaning data with some "bag of trick" before training
    - training the model for word embeddings with "cbow" model
    - getting threshold regarding ClimaText dataset
    - exracting most smiliar quotes based on threshold
- [`ClimaTextBERT.ipynb`](./ClimaTextBERT.ipynb) - taking climate change quotes based of distilled BERT supervised model
    - training the model BERT model
    - evaulating the model with ClimaText dataset
    - exracting quotes using our model
- [`Enrichment.ipynb`](./Enrichment.ipynb) - in this notebook is provided all additional features
    - sentiment analysis
        - distil BERT model for sentiment analysis
        - state-of-the-art performance of ~93% accuracy
    - claims misinformation prediction using CARDS
        - model based on RoBERTa architecture
        - classify quote on 17 classes of different misinformation
- [`ADAlysis.ipynb`](./ADAlysis.ipynb) - the main file, contains all the details of our ADAlysis

## Data story
On the following link you can find the whole data story about our project: https://teamnerf.github.io/ADA_Data_Story (reading time: 15 min)
## Authors
- Carevic Filip
- Maid Edvin
- Mitic Natalija
- Pejic Radenko
