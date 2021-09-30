# ACoLi CoNLL libraries

The ACoLi CoNLL libraries are an aggregator repository for several tools for processing, manipulating and transforming TSV formats developed at the Applied Computational Linguistics Lab at Goethe University Frankfurt, Germany.

## Table of Contents

  * [What it does](#what-it-does)
    + [Merging and retokenizing annotations](#merging-and-retokenizing-annotations)
    + [Parsing CoNLL into graphs and back](#parsing-conll-into-graphs-and-back)
    + [Visualizing and querying CoNLL annotations](#visualizing-and-querying-conll-annotations)
    + [Other tools](#other-tools)
  * [Setting it up](#setting-it-up)
  * [Related tools](#related-tools)
  * [Acknowledgements](#acknowledgements)

## What it does

### Merging and retokenizing annotations

CoNLL-Merge (`conll-merge/`): Given two or more annotations of the same text, say, `abc.conll` with 10 columns and `xyz.conll` with 5 columns, align and concatenate them such that for every word from `abc.conll`, the corresponding row first has the original annotation from `abc.conll`, followed by the annotations from `xyz.conll`, i.e., 14 columns in total (the `WORD` column from `xyz.conll` that is used for alignment is suppressed by default). 

If the files cannot be aligned, the user can chose from different conflict resolution strategies. By default, CoNLL-Merge will put unaligned words into separate rows and fill up the columns with the placeholder symbol `?` to indicate alignment errors. Alternatively, the user can chose to enforce the tokenization of the first file onto the second, to split tokens from all files into their smallest common elements, to use minimal edit distance to find the most likely alignment, or any combination of these strategies.

Note that the alignment is sufficiently robust to be applied off-the-shelf in the following non-standard constellations:
- retokenize a previously annotated text (e.g., undo the tokenization of an annotation tool)
- the same text has been processed by different NLP tools that did some alternations to the primary data (e.g., escape certain symbols)
- the same text is used, but using different encodings (e.g., XML entities vs. UTF-8 characters)
- the same text is used, but tokenized according to different principles, e.g., one version with whitespace tokenization (`don't` `go`), one with Penn-style tokenization (`do` `n't` `go`)
- different editions of the same text with differences in wording (e.g., different manuscripts of a historical text)

### Parsing CoNLL into graphs and back

CoNLL-RDF (`conll-rdf/`): Given a CoNLL file, break it into sentences and expose every sentence (and, optionally, its context) as an RDF graph. Manipulate it with SPARQL, e.g., enrich it with links to an external knowledge base. Serialize back into a CoNLL format, an RDF representation or other corpus formats.

In combination with CoNLL-Merge (see below), this allows complex transformations of linguistic annotations, e.g., to derive 

We see the primary use of CoNLL-RDF in aggregating and transforming the output of NLP tools and in complex aggregation tasks over heterogeneous input annotations, e.g., syntax and semantics. Sample applications:

- Given corpus data in one CoNLL format, convert it into another CoNLL format (see [CoNLL-Transform](https://github.com/acoli-repo/conll-transform))
- Given the output of one NLP tool, convert it for consumption of another NLP tool (see our [Flexible Integrated Transformation and Annotation Engineering platform [FINTAN]](https://github.com/Pret-a-LLOD/Fintan) and the NLP workflow management system [Teanga](https://github.com/Pret-a-LLOD/teanga))
- Given a WordNet in a TSV format, transform it to OntoLex-Lemon (see our edition of the [Open Multilingual WordNet](https://github.com/acoli-repo/acoli-dicts/tree/master/stable/omw)
- Given a dictionary with annotations according to scheme A, use an external ontology to map its annotations to scheme B (see our edition of the [Apertium Dictionaries](https://github.com/acoli-repo/acoli-dicts/tree/master/stable/apertium)
- Given a corpus with concurrent annotations from PropBank and Universal Dependencies, merge both annotations using CoNLL-Merge, transform the aggregate graph into a new corpus formalism (see our [RRG corpus](https://github.com/acoli-repo/RRG))
- Given a corpus with parts of speech and a lexicon, perform rule-based parsing and add lexical features (see our [Middle High German corpus](https://github.com/acoli-repo/germhist))

Special features missing from generic TSV/CSV parsers is that we support extensions of the CoNLL data model to account for syntactic dependencies (as object properties), chunk annotations (IOBES/BIO schemata), trees (phrase structure syntax), XML markup (e.g., for text structure annotation), and special extensions for semantic role labelling (one additional column per predicate per sentence).

### Visualizing and querying CoNLL annotations

There are plenty of CoNLL visualizers around, however, most of these are limited to a specific CoNLL dialect, e.g., CoNLL-U, and operate either memory-based (Brat) or against a relational backend (CWB). A downside of these that they are hard to adapt for changes in the data model, e.g., the introduction of another annotation layer. As an alternative, we allow to operate against an RDF triple/quad store as a backend.

CQP4RDF (`cqp4rdf/`): Visualizing and querying CoNLL annotations *as graphs*. 

As the use of RDF technology is still somewhat uncharted territory for corpus linguists, we support a classical corpus query language, CQP, for querying the backend. However, it is possible to perform queries beyond the expressivity of CQP by extending CQP statements with SPARQL fragments.

### Other tools

- CoNLL-Transform (`conll-transform/`): lightweight program to autoconfigure CoNLL-RDF for transforming one CoNLL format into another.
- XML2CoNLL (`xml2conll/`): generic converter from XML format(s) to CoNLL, can be used to feed XML into CoNLL-Merge, CoNLL-RDF or CQP4RDF.

## Setting it up

Note that this repo uses the `submodule` functionality of git and that the aggregator repository is unpdated occasionally, only. To retrieve the most up-to-date versions, clone this repo using

    $> git clone --recurse-submodules --remote-submodules https://github.com/acoli-repo/conll

For updating an existing installation in the directory `./conll/`, run

    $> cd ./conll/
    $> git submodule update --recursive .
  
Note that these repositories do not have strong interdependencies in the aggregator, but that this has been mostly created to faciliate a quick-and-easy local setup of all components of the ACoLi CoNLL Libraries. For development, we recommend to work within the submodule repositories directly.

## Related tools

Please see [Related.md](./Related.md) for an overview over related tools.

## Acknowledgements

If you use the ACoLi CoNLL Libraries, please refer to our reference publication:

* Chiarcos, C. & Schenk, N. (2018), [The ACoLi CoNLL Libraries: Beyond Tab-Separated Values](http://www.lrec-conf.org/proceedings/lrec2018/pdf/869.pdf), In: Proceedings of the Eleventh International Conference on Language Resources and Evaluation (LREC 2018), Miyazaki, Japan, May 7-12, 2018, p.571-576.

If you work with individual components, please see the respective sub-folder for attribution and licensing information.
