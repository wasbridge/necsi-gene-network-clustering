# necsi-gene-network-clustering

## Requirements
1. Python3 (3.7)
2. Pandas
3. NumPy
4. matplotlib
5. scipy
6. (optional) igraph (required for analysis-network)

## Preparation
In data folder unzip both data files which are zipped (this is because GitHub won't let us upload huge files)

## Order of operations
1. Run analysis notebook to generate the list of genes products which are statistically significantly different between stage 1 and stage 2 tumors, stage 1 and stage 3 tumors and stage 2 and stage 3 tumors

2. Run vizualization-gephi-simplified notebook to generate the graph (gml file) of one of the sets of nodes identified by step 1

2.a Open gml file in Gephi to produce results (using CircularPack layout to generate clusters based on modularity) .gephi files in out folder have all settings we used

3. (Optional) run analysis-network to demonstrate scale free network 


## Notes: 
Experiments were done with graphviz and igraph plotting, neither panned out as well as gephi, old programs are denoted by old_ prefix

simplified means we're not plotting the whole network, just a subset of the statistically significant gene prodcuts

simplified networks don't show connections between nodes which are indirectly connected through non statistically significant nodes

For example:
Assume a,c,h,i are significant (the rest aren't)

Full Network:
|-------------|
|---|         |
a-b-c-d-e-f-g-h-i
|_____|

Simplified Network:
a-c
|
h_i

The problem here is that even though a is connected to i and c is connected to i (indirectly) we don't represent that in the simplified network, but in reality we believe this isn't significant because the shortest pathway won't be affected, and its the shortest pathway that characterizes behavior