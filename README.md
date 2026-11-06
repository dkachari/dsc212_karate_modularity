# dsc212_karate_modularity
The aim of this assignment is to divide the Karate Club graph into communities using recursive spectral partitioning and then examine the roles of individual nodes using four network metrics.
# DSC212: Modularity on the Karate Club Graph

## Contents

- `DSC212_Karate_Modularity.ipynb`: complete report, implementation, executed outputs, figures, and references.
- `results/`: figures, partition history, node metrics, and validation results.
- `requirements.txt`: Python dependencies.

## Run

Open the notebook in Jupyter or Google Colab and run all cells from the beginning. Its first code cell installs missing dependencies using the active Python interpreter. Internet access is required only if packages are missing. The dataset is included with NetworkX. Generated files are written to the `results/` directory.

For a local environment, from this folder run:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m jupyterlab
```

Select the environment's Python kernel, restart it, run all cells, and save the notebook. If a previous run failed at an import, restart and run from the beginning: later cells depend on the graph and variables created during setup.

## Method

The unweighted 34-node, 78-edge graph is partitioned by recursive leading-eigenvector sign splits. Original degrees and edge count are retained throughout. The subgroup matrix includes the diagonal row-sum correction, and a split is accepted only when its actual global modularity gain is positive. No built-in community-detection algorithm is used.

Metrics are computed on both the original graph and each current induced community. The original-graph values remain constant, whereas the within-community values change with the partition. This distinction is explained in the report.

## Results

| Accepted-split iteration | Number of communities | Modularity |
|---|---:|---:|
| 0 | 1 | 0.00000000 |
| 1 | 2 | 0.37146614 |
| 2 | 3 | 0.37269888 |
| 3 | 4 | 0.39340894 |

Final community sizes: 7, 9, 12, and 6. The first split matches 33 of 34 historical club labels. Validation checks confirm valid partitions, agreement with NetworkX modularity, and strictly positive accepted gains. Exhaustive checks find no improving bisection within any final community; global optimality is not claimed.

## Reference

M. E. J. Newman (2006). Modularity and community structure in networks. *PNAS*, 103(23), 8577–8582. https://doi.org/10.1073/pnas.0601602103

Dataset: Zachary (1977), through NetworkX. Full references and mathematical derivations appear in the notebook.


## Student details
Name: Debojit Kachari

Roll number: IMS25061

## AI-use acknowledgement
AI tools were used to assist with parts of the code, simplify the logic and explanations, and check the results.
