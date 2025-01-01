# symNMF

## Description
This repository contains a university course project and contains the implementation of a clustering algorithm based on Symmetric Non-negative Matrix Factorization (SymNMF). The project includes Python and C components, and it compares the performance of SymNMF with K-means clustering on various datasets.

### Project Components
#### 1. SymNMF Algorithm
The SymNMF algorithm clusters data points by factorizing a normalized similarity matrix into a low-rank, non-negative representation. The main steps include:
1. Constructing the similarity matrix (A).
2. Computing the diagonal degree matrix (D).
3. Normalizing the similarity matrix to produce (W).
4. Optimizing the matrix (H) using the Frobenius norm minimization.

The algorithm iteratively updates H until convergence based on a defined criterion (maximum iterations or Frobenius norm difference threshold).

#### 2. Implemented Files
- `symnmf.py`: Python interface for executing SymNMF-related computations.
- `symnmf.c`: C implementation of core computations.
- `symnmfmodule.c`: Python C API wrapper to integrate C functions into Python.
- `symnmf.h`: C header file containing function prototypes.
- `analysis.py`: Script to compare SymNMF with K-means clustering using silhouette scores.
- `setup.py`: Python setup file for building the C extension.
- `Makefile`: Script for building the C program.

## Usage
### Building everything
To build the Python extension module:
```sh
python3 setup.py build_ext --inplace
```
To compile the C program:
```sh
make
```

### Python Program (`symnmf.py`)
This program accepts command-line arguments to compute specific outputs:
1. `k`: Number of required clusters.
2. `goal`: Task to perform:
   - `symnmf`: Perform full SymNMF and output H.
   - `sym`: Compute and output the similarity matrix.
   - `ddg`: Compute and output the diagonal degree matrix.
   - `norm`: Compute and output the normalized similarity matrix.
   - `file_name`: Path to the input file containing data points.
```sh
python3 symnmf.py <k> <goal> input.txt
```

### C Program (`symnmf.c`)
The C implementation supports:
- Computing the similarity matrix, diagonal degree matrix, or normalized similarity matrix based on the goal provided as a command-line argument.
```sh
./symnmf sym input.txt
```

### Analysis Script (`analysis.py`)
Compares SymNMF and K-means clustering using silhouette scores. Takes the number of clusters and input file as arguments.
```sh
python3 analysis.py <#clusters> input.txt
```

## Output
All matrix outputs are comma-separated, with each row on a new line. Values are formatted to four decimal places.

Example output:
```sh
0.0600,0.0100
0.0100,0.0500
0.0100,0.0400
```

