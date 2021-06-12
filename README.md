# Classifying space with ML

This repository contains the data and some of the code from machine learning classification experiments that explore how unsupervised node embedding methods may allow computational access to architectural spatial configurations represented as graph structures. The research was conducted as part of my Master's thesis in computational design. 

### Data set

A data set specifically created for classification experiments by Ferrando, Dalmasso, Mai and Cardoso Llach [(Ferrando et al., 2019)](http://cumincad.scix.net/cgi-bin/works/Show?cf2019_014) is used. The [original data set](https://github.com/c0deLab/ML-architectural-analytics) contains CAD plans and supporting data of 19 monastery and 20 mosque complexes modeled by the researchers. `data/txt` contains the form of the original data that used by me. However, the linked repository has other forms of the data, including the CAD files and source material for the CAD files. 

### Code

`notebooks` contains a series of notebooks that prepare the base data for the experiments. First, each building is saved in a JSON format suitable for loading into the [NetworkX](https://networkx.org/documentation/stable/index.html) network analysis package. Subsequent notebooks add graph theoretic attributes to the nodes (representing rooms) and graphs (representing buildings). Vector encodings created with [this implementation](https://github.com/eliorc/node2vec) of the [node2vec](http://snap.stanford.edu/node2vec/) framework are also added as node and graph attributes. The vector representing a whole graph is the mean of the node vectors of that graph. Finally, the JSON files are saved as CSV files for the machine learning classification experiments. The experiments were conducted on the Weka tool bench; therefore, the code for the experiments are not included here.

### Some details

Vectors encodings are created using two sets of node2vec *p* and *q* parameters. The duplets *p*=1 and *q*=2, and *p*=1 and *q*=0.5, create embeddings that capture homophilic and structural qualities, respectively, according the [original research paper](https://arxiv.org/abs/1607.00653).

Three vector spaces are created: buildings encoded as separate graphs, buildings encoded as disconnected components within a single graph, and buildings encoded while connected to a common ground node within a single graph.

<!-- 
Future work:
Develop grasshopper code to extract more information from the original CAD files. Could be a good opportunity for more sophisticated grasshopper coding and interaction.

Set it up as a template for further work with other encoding algorithms. GEM

Figure out how the GAT repository is working and emulate that.
-->
