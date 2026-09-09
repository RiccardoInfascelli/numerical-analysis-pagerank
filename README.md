# Numerical Analysis of PageRank

This repository contains the implementation, numerical experiments, and final report for a project on the numerical analysis of the **PageRank algorithm**.

The project focuses on the power method, the effect of the damping factor, sparse and matrix-free computation, and an application to the **HEP-TH scientific citation network**.

## Project Structure

```text
numerical-analysis-pagerank/
├── README.md
├── requirements.txt
├── notebooks/
│   └── pagerank_analysis.ipynb
├── data/
├── assets/
└── report/
    └── report.pdf
```

- `notebooks/`: Jupyter notebook containing the implementation and numerical experiments.
- `data/`: HEP-TH citation-network data and metadata.
- `report/`: final project report.
- `requirements.txt`: Python dependencies required to run the notebook.
- `assets/`: figures and visualizations used in the documentation.

## Numerical Method

PageRank is formulated as the stationary distribution of the Google matrix and computed using the **power method**.

Instead of explicitly constructing the dense Google matrix, the implementation exploits the sparsity of the hyperlink matrix and handles the dangling-node and teleportation corrections in a matrix-free way.

For a graph with `n` nodes and `m` edges, the implementation requires:

- **O(m + n)** computational work per iteration;
- **O(m + n)** total memory.

This makes the implementation suitable for substantially larger graphs than the corresponding dense formulation.

## Dataset

The experiments use the **High Energy Physics Theory (HEP-TH) citation network** distributed by the Stanford Network Analysis Project (SNAP).

In the directed graph, an edge from paper `i` to paper `j` indicates that paper `i` cites paper `j`.

After preprocessing the dataset by removing duplicate edges and self-citations, the network used in the experiments contains:

- **27,769 papers**
- **352,768 directed citation links**

## Numerical Results

The implementation was first validated on a small directed graph by comparing the power iteration with independent numerical formulations.

The sparse matrix-free implementation produced PageRank vectors equivalent to the dense formulation up to floating-point precision.

To study computational performance, dense and sparse implementations were compared on synthetic directed graphs of increasing size.

The results show that the sparse matrix-free formulation becomes increasingly advantageous as the graph size grows, because it avoids constructing and multiplying the dense Google matrix.

![Sparse PageRank speedup](assets/sparse_speedup.png)

*Speedup of the sparse matrix-free implementation relative to the dense formulation.*

The algorithm was then applied to the HEP-TH citation network to compare PageRank with standard citation-count rankings.

For a damping factor of `0.50`, PageRank converged in **20 iterations**, with a final residual of approximately `5.59e-9`.

The Spearman correlation between PageRank and citation count was approximately **0.868**, showing that the two rankings are strongly related but capture different aspects of paper importance.

The notebook also includes a dynamic PageRank update experiment. Starting from an existing directed graph, new nodes and links are added, and different initialization strategies are compared for recomputing PageRank on the updated graph.

The experiment compares cold start, warm start, and aggregation-assisted refinement. The warm start reuses the PageRank vector computed on the old graph, while the aggregation-based strategy first builds a reduced problem and then uses its solution to initialize a refinement step on the full updated graph.

This part of the project illustrates how previous computations and graph structure can be exploited to reduce the cost of PageRank updates, without changing the final PageRank model.

## Running the Project

Clone the repository:

```bash
git clone https://github.com/RiccardoInfascelli/numerical-analysis-pagerank.git
cd numerical-analysis-pagerank
```

Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
```

On Windows:

```bash
.venv\Scripts\activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

Then open:

```text
notebooks/pagerank_analysis.ipynb
```

using Jupyter Notebook, JupyterLab, or Visual Studio Code.

## Report

The complete project report is available at:

```text
report/report.pdf
```

It contains the mathematical formulation of PageRank, the sparse and matrix-free implementation, convergence analysis, numerical experiments, performance benchmarks, the application to the HEP-TH citation network, and the dynamic PageRank update experiment.

## Technologies

- Python
- NumPy
- SciPy
- Jupyter

## Author

**Riccardo Infascelli**  
M.Sc. High Performance Computing Engineering  
Politecnico di Milano