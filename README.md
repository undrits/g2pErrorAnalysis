Error analysis tool for grapheme to phoneme (g2p) conversion
============================================================

This tool performs a fine-grained error analysis of a G2P model. It reports a
performance matrix of a test output generated by a G2P model.

Under this error analysis process, each test record generated from a G2P model
is evaluated under two criteria. ⋅⋅\* if the hypothesized form matches the
corpus prediction or not. ⋅⋅\* if the hypothesized form adheres to grammatical
rules of the language.

The output of the tool is a two dimentional matrix as shown below-
```
               | CG Match  |   CG Not Match |
---------------|-----------+----------------|
Pron Match     |  79.34    |      05.01     |
Pron Not Match |  13.15    |      02.50     |
```
Here the numbers represents percentage of test records falling under X-section
of each category.

Prerequisites
-------------

### Library

install pynini
install prettytable

``` {.bash}
conda install -c conda-forge pynini
pip install prettytable
```
### Data

To run this tool following data items are required -

⋅⋅\* Covering grammar : Each line contain grapheme and their corresponding
pronunciation seperated by a tab. Refer [adyghe_cg.tsv](data/adyghe_cg.tsv) file
inside data folder for more detail.

⋅⋅\* Test output : This file contains three attributes in each line seperated by
a tab. The attributes are - orthography, expected pronunciation, and
hypothesized pronunciation (placed in the same order). Refer
[test.tsv](data/test.tsv) file inside data folder for more detail.

Suggested workflow
------------------

clone repo

    cd g2pErrorAnalysis
    python erroranalysis.py --cg_path data/adyghe_cg.tsv --test_path data/test.tsv

Reference
---------

Gorman, Kyle. 2016. [Pynini: a Python library for weighted finite-state grammar
compilation.](https://www.aclweb.org/anthology/W16-2409) In Proceedings of the
SIGFSM workshop on statistical NLP and weighted automata, 75--80. Berlin:
Association for Computational Linguistics.
