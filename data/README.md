# HEP-TH Citation Network Dataset

This directory contains the High Energy Physics Theory citation network
distributed by the Stanford Network Analysis Project (SNAP).

## Files

- `cit-HepTh.txt.gz`: directed citation network
- `cit-HepTh-dates.txt.gz`: paper submission dates
- `cit-HepTh-abstracts.tar.gz`: paper metadata, including titles, authors and abstracts

## Graph interpretation

Each node represents a scientific paper.

A directed edge from paper `i` to paper `j` means that paper `i` cites paper `j`.

The original SNAP dataset contains:

- 27,770 nodes
- 352,807 directed edges
- papers submitted between January 1993 and April 2003

The notebook performs additional preprocessing, including the removal of
duplicate edges and self-citations. Therefore, the processed graph used in
the numerical experiments may contain slightly fewer nodes and edges.

## Source

Stanford Network Analysis Project:

https://snap.stanford.edu/data/cit-HepTh.html

The dataset was originally released as part of the 2003 KDD Cup.
