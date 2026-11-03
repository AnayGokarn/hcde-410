# HCDE 410 Assignment 2: Exploring sources of bias in data

This folder holds my work for Assignment 2 in HCDE 410: Human Data Interaction. The assignment looks at the Wikipedia Talk Corpus, a dataset of Wikipedia talk-page comments that crowdworkers labelled for toxicity, aggression, and personal attacks. The goal is to find ways the data might be wrong or biased, and to think about what that means for a hostile-speech detector like the Perspective API.

## What's in this folder

| File or folder | What it is |
|---|---|
| `hcde410-a2.ipynb` | The assignment notebook, with code, outputs, and written answers. |
| `wikipedia_datasets/` | The three worker demographics files (toxicity, aggression, attack). |
| `toxicity_data/toxicity_annotations.tsv` | All 1.6 million toxicity labels, downloaded from Figshare. Used for Q9-Q12. |
| `a2_all_annotator_demographics.csv` | Created by the notebook: the combined worker demographics from Part 1. |
| `a2_toxicity_comment_review.csv` | Created by the notebook: my agree/disagree notes on 60 sample comments (Q13). |
| `LICENSE.md` | The license for the course's code (see below). |

## About the data

The data comes from the Wikimedia [Detox research project](https://meta.wikimedia.org/wiki/Research:Detox/Data_Release). It is published on Figshare in three parts:

- [Wikipedia Talk Labels: Toxicity](https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Toxicity/4563973) (doi: 10.6084/m9.figshare.4563973)
- [Wikipedia Talk Labels: Aggression](https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Aggression/4267550) (doi: 10.6084/m9.figshare.4267550)
- [Wikipedia Talk Labels: Personal Attacks](https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Personal_Attacks/4054689) (doi: 10.6084/m9.figshare.4054689)

The datasets were created by Ellery Wulczyn, Nithum Thain, and Lucas Dixon. The [documentation page](https://meta.wikimedia.org/wiki/Research:Detox/Data_Release) explains each file and column.

Some things to know before using the data:

- **The aggression and attack demographics files are exact copies of each other.** The documentation doesn't say this.
- **`worker_id` is not unique across datasets.** The same ID can belong to different people in the toxicity and attack/aggression files. Only join toxicity labels to toxicity workers.
- **Demographics are missing for some workers.** About 16.5% of the workers who labelled the toxicity data have no demographic data, and about 2% of the workers we do have are missing an age group.
- **The comments contain offensive language**, including profanity, slurs, and threats. Parts of the notebook print some of these comments.

## License and terms

- **Data:** The three Figshare datasets are released under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/) (public domain). The comment text originally comes from Wikipedia talk pages, which Wikipedia publishes under [CC BY-SA](https://creativecommons.org/licenses/by-sa/4.0/). If you reuse the comments, credit Wikipedia.
- **Code:** The starter code and notebook template are by Jonathan Morgan and Brock Craft, under the MIT License in `LICENSE.md`.

## How to re-run the notebook

1. **Install Python 3** (I used 3.13) and the packages the notebook needs:

   ```bash
   pip install notebook pandas matplotlib
   ```

2. **Get the toxicity annotations file** if it isn't already in `toxicity_data/`. Download `toxicity_annotations.tsv` (36 MB) from the [Toxicity Figshare page](https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Toxicity/4563973) and put it in a folder called `toxicity_data` next to the notebook. Or run:

   ```bash
   mkdir toxicity_data
   curl -L -o toxicity_data/toxicity_annotations.tsv https://ndownloader.figshare.com/files/7394539
   ```

3. **Open and run the notebook.** Start Jupyter from this folder, open `hcde410-a2.ipynb`, and choose *Run All*:

   ```bash
   jupyter notebook hcde410-a2.ipynb
   ```

   Or run it from the command line without opening it:

   ```bash
   jupyter nbconvert --to notebook --execute --inplace hcde410-a2.ipynb
   ```

Notes:
- The notebook must stay in the same folder as `wikipedia_datasets/`, `toxicity_data/`, because it uses relative paths.
- The Q9-Q12 cells load 1.6 million rows, so they can take a minute or two.
- The spot check in Part 1 picks 10 random worker IDs, so its output changes each run. Everything else gives the same results every time.