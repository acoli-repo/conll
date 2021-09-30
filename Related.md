# Related external tools

The ACoLi CoNLL Libraries provide means of merging, transformation and querying of CoNLL and other TSV data.

Special features are:
- support for CoNLL-specific extensions of the conventional TSV/CSV format
- applicable to any CoNLL dialect
- out-of-the-box parsing of CoNLL into RDF graphs 

However, more specialized tools for individual dialects or purposes may be preferred at times. Below, you can find an (incomplete) list.

## Visualization and editing of CoNLL/TSV data

- [Terminal-based CoNLL-file viewer](https://lindat.mff.cuni.cz/repository/xmlui/handle/11234/1-2514) (last version 2017, probably CoNLL-U only)
- [CoNLL-U editor](https://github.com/Orange-OpenSource/conllueditor) (CoNLL-U only)
- [CoNLL-X utils](https://github.com/danieldk/conllx-utils) (CoNLL-X only, incl. viewer; note that their "merge" means to append rows, not to append colums as in CoNLL-Merge)  

## Parsing of CoNLL/TSV data into RDF

- [survey article](https://medium.com/datafabric/a-practical-review-of-non-rdf-to-rdf-converters-51686338927f) about CSV-to-RDF parsers (2018)
- [TARQL](https://tarql.github.io/) small library for the conversion of CSV data streams into RDF using SPARQL. Can be used as an alternative to the CoNLL-RDF Stream Extractor for cases where no relations between rows are required (e.g., for lexical data).

## Parsers of CoNLL/TSV data for different programming languages

- [Python parser for CoNLL-U](https://github.com/EmilStenstrom/conllu): Python, not streamable; customizable to other CoNLL dialects, see [example](https://dataplatform.cloud.ibm.com/data/notebooks/converter/assets/0e615c46-5e4c-496f-9374-25dde48b46d0?access_token=aa16e0d5e3447e3979158b5f5c7de5436b3381424311470ded1686d90835da1e&project=0ea3900c-acb0-4c29-a1f7-efe42dcacd21); possibly restricted to fixed-width formats, i.e., no SRL annotation
- [NLTK CoNLL Reader](https://www.nltk.org/_modules/nltk/corpus/reader/conll.html): Python, customizable, column types: WORDS, POS, TREE, CHUNK, NE, SRL, IGNORE; no support for dependencies
- [pyconll](https://github.com/pyconll/pyconll): Python, CoNLL-U only
- [colonel](https://github.com/nlpodyssey/colonel): Python, CoNLL-U only
- [conllx (Rust)](https://docs.rs/conllx/0.12.1/conllx/): Rust parser, CoNLL-X only
- [R parser](https://rdrr.io/cran/NLP/man/CoNLLTextDocument.html): R parser, customizable; apparently restricted to fixed-width formats, i.e., no SRL annotation
