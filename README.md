# ACoLi CoNLL libraries

The ACoLi CoNLL libraries are an aggregator repository for several tools for processing, manipulating and transforming TSV formats developed at the Applied Computational Linguistics Lab at Goethe University Frankfurt, Germany.

Note that this repo uses the `submodule` functionality of git and that the aggregator repository is unpdated occasionally, only. To retrieve the most up-to-date versions, clone this repo using

  $> git clone --recurse-submodules --remote-submodules https://github.com/acoli-repo/conll

For updating an existing installation in the directory `./conll/`, run

  $> cd ./conll/
  $> git submodule update --recursive .
  
Note that these repositories do not have strong interdependencies in the aggregator, but that this has been mostly created to faciliate a quick-and-easy local setup of all components of the ACoLi CoNLL Libraries. For development, we recommend to work within the submodule repositories directly.
