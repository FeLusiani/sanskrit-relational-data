# Sanskrit relational dataset

[This dataset](https://www.kaggle.com/federicolusiani/sanskrit-relational-data) contains the data extracted from the CoNLL-U files in [this dataset](https://github.com/OliverHellwig/sanskrit/tree/master/dcs/data) (latest commit at time of writing: [2dd79c7](https://github.com/OliverHellwig/sanskrit/tree/2dd79c71576ddeff47573a3c4b953cb2ef92af1c)).

The `.conllu` files have been parsed into `pandas.DataFrame` objects (relational format) and stored as `.feather` files, allowing efficient and flexibile manipulation of the data.

## Details

The `.conllu` files in each directory of the original dataset have been parsed and merged into two files: `words.feather` and `text_lines.feather`.

Each `word` is stored with the following fields:
- *ID*, *FORM*, *LEMMA*, *UPOS*, *XPOS*, *FEATS*, *HEAD*, *DEPREL*, *DEPS*, *MISC*, *LEMMA_ID*, *unsandhied_form*, *semantic_id*, *text_line_id*.

These are are the original fields present in the `.conllu` files, with the addition of `text_line_id`, which can be used to retrieve infos about the text line containing the word.

Each `text_line` is stored with the following fields:
- *text_id*, *chapter_id*, *text_line*, *text_line_id*, *text_line_counter*, *text_line_subcounter*.

The `texts.csv` files and `chapters.csv` files have been produced from DCS main database dump linked [here](https://github.com/OliverHellwig/sanskrit/tree/master/dcs/data), and can be used to retrieve infos about the text and chapter containing each text line.

## Merged data

The structure of the dataset mirrors the one of the original containing `.conllu` files. Each pair of `words.feather` and `text_lines.feather` is the aggregation of the `.conllu` files that were present in the corresponding directory.

The separate `.feather` files can be easily merged together (as shown in `code/sanskrit.ipynb`). The output of this merge is available [here](https://www.kaggle.com/federicolusiani/sanskrit-relational-data).

## Code
The code used to parse the original `.conllu` files has been added for reproducibility.

## Acknowledgments
Credit goes to the creators of the original dataset: Oliver Hellwig: Digital Corpus of Sanskrit (DCS). 2010-2021.