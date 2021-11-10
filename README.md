# Do US politicians care about climate change?
<!-- omit in toc -->

This team project is a part of the [Applied Data Analysis 2021](https://dlab.epfl.ch/teaching/fall2021/cs401/) curriculum at the EPFL.

The purpose of this file is to explain the project and help you navigate this repo.

## Table of Contents
- [Abstract](#abstract)
- [Goal](#goal)
- [Data](#data)
- [Methods](#methods)
- [Proposed timeline](#proposed-timeline)
- [Navigating the repo](#navigating-the-repo)
- [Authors](#authors)


## Abstract
Wildfires, hurricanes, droughts - just another regular year on planet Earth. The common factor is none other than **climate change**.
<br><br>
Climate change is a topic that deeply concerns all of us and potentially the most devastating problem that the humanity has ever faced. Although the impacts of global warming are sporadically occurring, thus providing a false sense of comfort, it is important to address these issues and take action. This is a human responsibility but nonetheless a political one as well.
<br><br>
For that reason, we want to analyze how concerned are the US politicians. Are they raising awarenes about the global warming and is fighting climate change a part of their agenda? Or perhaps, is this a topic they would rather sweep under the rug.
<br>
Moreover, we want to investigate whether there are any correlations between specific demographics (e.g. age, education, state of domicile, etc.) and the attitude towards climate change.


## Goal
In this project, we aim to analyze quotes from US politicians concerning climate change. This should allow us to paint a picture about the importance of climate change from a politician's point of view.
<br><br>
In addition to this, we strive to provide answers to following questions:
- How often does a specific politican give statements about climate change. In other words, what is the ratio between climate change and non-climate change quotes?
- Which politician talks the most about climate change?
- Can we relate the opinion about climate change towards specific demographic parameters?
- At what points in time do politicians talk (more) about climate change (e.g. immediately after a disaster)?
- Which politicians are the first to forget about the problems related to climate change?
- and many more...

Certainly, all the above-mentioned questions should be addressed in respect to political parties as well.

## Data
The data we will use for our analysis consists of:
- quotes from US politicians published during the period from 2015 to 2020 - acquired from the [Quotebank dataset](https://dlab.epfl.ch/people/west/pub/Vaucher-Spitz-Catasta-West_WSDM-21.pdf)
- additional metadata about the speakers in the Quotebank dataset - acquired from the [Wikidata knowledge base](https://www.wikidata.org/wiki/Wikidata:Main_Page) and available as a `speaker_attributes.parquet` file on [Google Drive](https://drive.google.com/drive/folders/1VAFHacZFh0oxSxilgNByb1nlNsqznUf0). In addition to this `.parquet` file, if some extra (Wiki)data is needed it will be acquired through Wikidata SPARQL queries.


Given that the Quotebank dataset comprises a huge amount of quotes, it is crucial to filter out all those quotes that are not said by US politicians.
<br>
This is feasible by:

- removing unnecessary speakers from the `.parquet` file
- merging the `.parquet` file with the Quotebank dataset

## Methods
<!-- todo -->

## Proposed timeline

This project should be completed by December 17th. Our proposed timeline can be found in the table below:

| Period                 | Description               |
| ---------------------- | ------------------------- |
| 13. Nov - 19. Nov      | Extracting quotes about climate change                                               |
| 20. Nov - 27. Nov      | Sentiment analysis of extracted quotes                                               |
| 28. Nov - 07. Dec      | Data analysis and answering questions                                            |
| 08. Dec - 11. Dec      | Creating data story for visual representation of project's findings                 |
| 12. Dec - 17. Dec      | Final revisions           |
| 17. Dec                | Project submission        |

## Organization within the team
<!-- todo -->

## Navigating the repo
<!-- todo -->

## Authors
- Carevic Filip
- Maid Edvin
- Mitic Natalija
- Pejic Radenko
