# German Reddit stance dataset

This repository contains a dataset of Reddit comments from the German-speaking subreddit r/de, focusing on discussions about railway worker strikes in Germany from November to December 2023.  The dataset was build to evaluate the abilities of LLMs such as GPT-4 or Claude 3.5 Sonnet for stance classification of German Reddit comments.


## Dataset Overview

- **Source**: Comments extracted from submissions to r/de subreddit
- **Time period**: November 9, 2023 to December 19, 2023
- **Total comments**: 1150
- **Number of submissions**: 7
- **Language**: German

## Dataset Structure

The dataset is organized as a series of JSON files, each representing a single submission and its associated comments. The file names correspond to the unique submission IDs.

### Submission Object Structure

| Field | Description | Example |
|-------|-------------|---------|
| id | Unique identifier | 17v3qsh |
| title | Submission title | Deutsche Bahn: Lokführergewerkschaft GDL kündigt Streik an |
| score | Submission score | 349 |
| created | Creation date and time | 2023-11-14 15:45:00 |
| url | URL to the posted news article | https://www.tagesschau.de/eilmeldung/eilmeldung-7516.html |
| author | Author username | u/Digag |
| branches | List of top-level comment objects | [Comment objects] |

### Comment Object Structure

| Field | Description | Example |
|-------|-------------|---------|
| id | Unique identifier | k97ud84 |
| author | Author username | u/Noodleholz |
| body | Comment text | Da bei uns die Bahn abwechselnd wegen... |
| created | Creation date and time | 2023-11-14 15:48 |
| score | Comment score | 123 |
| parent_id | ID of parent (submission or comment) | t3_17v3qsh |
| link_id | ID of submission | t3_17v3qsh |
| branches | Replies to the comment | [Comment objects] or [] |
| stanceOnSubmission | Stance towards submission | positive |
| stanceOnParent | Stance towards parent comment | negative |

## Data Collection and Processing

1. Raw data acquired from the ArcticShift project, which mirrors Reddit data.
2. Submissions filtered using keywords related to railway strikes.
3. Comments for selected submissions extracted recursively.
4. Deleted comments and their descendants removed to respect user privacy.
5. Data manually annotated for stances using a custom web application.

## Annotation Schema

Comments are annotated with two types of stances:

1. **Stance towards submission**: {positive, negative, neither, null}
   - Interpreted as: In Favor, Against, Neither
   - null indicates absence of annotation

2. **Stance towards parent comment**: {positive, negative, neither, null}
   - Interpreted as: Agrees, Disagrees, Neither
   - null indicates absence of annotation or top-level comment

## Ethical Considerations

- User names have been pseudonymized to protect privacy.
- Deleted comments and their descendants have been removed from the dataset.
- The r/de subreddit's rules were respected in the data collection process.

## Limitations

- Single annotator, which may introduce subjectivity.

## Usage and Citation

[Include information about how to cite the dataset and any usage restrictions
