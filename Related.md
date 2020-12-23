# Related external tools

(under construction)

## Visualization and editing of CoNLL/TSV data

- [Terminal-based CoNLL-file viewer](https://lindat.mff.cuni.cz/repository/xmlui/handle/11234/1-2514) (last version 2017, probably CoNLL-U only)
- [CoNLL-U editor](https://github.com/Orange-OpenSource/conllueditor) (CoNLL-U only)
- [CoNLL-X utils](https://github.com/danieldk/conllx-utils) (CoNLL-X only, incl. viewer; note that their "merge" means to append rows, not to append colums as in CoNLL-Merge)  

## Parsing of CoNLL/TSV data into RDF

- [survey article](https://medium.com/datafabric/a-practical-review-of-non-rdf-to-rdf-converters-51686338927f) about CSV-to-RDF parsers (2018)
- [TARQL](https://tarql.github.io/) small library for the conversion of CSV data streams into RDF using SPARQL. Can be used as an alternative to the CoNLL-RDF Stream Extractor for cases where no relations between rows are required (e.g., for lexical data).

## Conversion of CoNLL/TSV data for different libraries

- [Python parser for CoNLL-U](https://github.com/EmilStenstrom/conllu), parse CoNLL-U strings into nested Python dictionaries, not streamable
- [pyconll](https://github.com/pyconll/pyconll) (CoNLL-U only)
