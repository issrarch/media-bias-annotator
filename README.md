# News Media Bias Detection Using Machine Learning Algorithms
## Project Overview

News coverage significantly influences public opinion, discourse, and perceptions of current events. However, news media are rarely neutral or value-free; their reporting is shaped by organizational, economic, social and political factors that can introduce bias. This project leverages the **MBIC** (Media Bias Including Characteristics) annotated dataset — comprising 1,700 news statements sampled from various media outlets across the political spectrum — to analyze news bias at the sentence level.  

Our main objective is to **predict whether a news statement is likely to be labeled as biased or non-biased** using both textual features (such as the use of biased words, sentence length, and lexical complexity) and media outlet characteristics (such as political leaning, factual reporting, and reliability scores).

## Data

We use the `labeled_dataset` from the MBIC database, containing 1,700 sentences extracted from approximately 1,000 news articles published by eight media outlets across the political spectrum. The dataset covers 14 topics that reflect major events and social issues from January 2019 to June 2020.

To enrich our analysis, we integrated two additional datasets providing information on news outlets’ factual reporting tendencies and reliability scores. We merged these sources by media outlet, producing the dataset used for subsequent analysis: `new_labeled_dataset.csv`.

## Directory Structure

- **deliverables/**: Project proposal and documentation of the modeling approach.
- **exploratory_data/**: Scripts used to generate the final dataset (`new_labeled_dataset.csv`) and to perform exploratory analysis.
- **analysis/**: Script for building the modeling pipeline, including preprocessing, feature engineering, train-test splitting, model training, and evaluation.

## Getting Started

To get started, clone this repository and explore the scripts in the `exploratory_data` and `analysis` directories. All the data files are located in the `data` folder.

---



