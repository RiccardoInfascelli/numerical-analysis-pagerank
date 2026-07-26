# Numerical Analysis of PageRank

Project developed for the **Numerical Analysis for Machine Learning** course at Politecnico di Milano.

The project studies the PageRank algorithm from a numerical perspective. PageRank is implemented in Python, tested on directed graphs of different sizes, and applied to the HEP-TH scientific citation network.

## Contents

The project includes:

- basic and sparse PageRank implementations;
- treatment of dangling nodes and teleportation;
- power iteration and convergence analysis;
- study of the damping factor;
- comparison with an eigensolver;
- comparison with the equivalent linear-system formulation;
- performance comparison between dense and sparse implementations;
- application to the HEP-TH citation network;
- comparison between PageRank and citation count;
- analysis of publication year;
- identification of candidate scientific gems.

## Project structure

```text
NAML-PageRank/
├── README.md
├── requirements.txt
├── notebooks/
│   └ pagerank_analysis.ipynb
├── src/
├── data/
└── report/
    └── report.pdf
```

- `notebooks/`: Jupyter notebook containing the implementation and numerical experiments.
- `src/`: reusable Python functions, if separated from the notebook.
- `data/`: HEP-TH citation-network data and metadata.
- `report/`: final project report.
- `requirements.txt`: Python dependencies required to run the notebook.

## Installation

Clone the repository and enter the project directory:

```bash
git clone git@github.com:YOUR-USERNAME/NAML-PageRank.git
cd NAML-PageRank
```

Create a Python virtual environment:

```bash
python3 -m venv .venv
```

Activate the environment on macOS or Linux:

```bash
source .venv/bin/activate
```

Install the required packages:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Running the notebook

Open the project in Visual Studio Code or start Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
notebooks/pagerank_analysis.ipynb
```

When using Visual Studio Code, select `.venv` as the Python kernel.

## Dataset

The experiments use the **High Energy Physics Theory citation network** distributed by the Stanford Network Analysis Project.

In the directed citation graph, an edge from paper \(i\) to paper \(j\) means that paper \(i\) cites paper \(j\).

After removing duplicate edges and self-citations, the network used in the experiments contains:

- 27,769 papers;
- 352,768 directed citation links.

## Main numerical results

The PageRank implementation was first validated on a six-page directed graph. With damping factor \(\alpha=0.85\) and tolerance \(10^{-8}\), the power iteration converged in 33 iterations.

The sparse matrix-free implementation produced results equivalent to the dense formulation up to floating-point precision, while becoming significantly faster as the graph size increased.

On the HEP-TH citation network, using \(\alpha=0.50\):

- PageRank converged in 20 iterations;
- the final residual was approximately \(5.59 \times 10^{-9}\);
- the Spearman correlation between PageRank and citation count was approximately \(0.868\);
- 13 candidate scientific gems were identified;
- publication year and PageRank showed a moderate negative association.

## Report

The final report is available in:

```text
report/report.pdf
```

It contains the mathematical formulation, numerical methods, implementation details, experiments, discussion, and conclusions.

## Author

Riccardo Infascelli

