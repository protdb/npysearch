# npysearch-win

**npysearch-win** is a Windows-compatible fork of [npysearch](https://github.com/tamminenlab/npysearch) by Aditya Jeevannavar (Tamminen Lab).

The original package does not compile correctly on Windows with Python 3.10+. This fork patches the build system so that pre-built wheels can be installed directly on Windows 10/11 (64-bit) without requiring a C++ compiler.

- **Original project (GitHub):** https://github.com/tamminenlab/npysearch
- **Original project (PyPI/Test):** https://test.pypi.org/project/npysearch/

---

npysearch implements an efficient BLAST-like sequence comparison algorithm, written in C++11 and using native Python datatypes and bindings. npysearch is light-weight, fast, and dependency-free. The code base of npysearch is adapted from [nsearch](https://github.com/stevschmid/nsearch). An implementation of nsearch for R is available at [blaster](https://github.com/tamminenlab/blaster).

## Installation

### from PyPI (this Windows fork)

```
pip install npysearch-win
```

### from the original project (Linux / macOS)

```
pip install npysearch
```

### from conda-forge (original)

```
conda config --add channels conda-forge
conda config --set channel_priority strict
conda install npysearch
```

### from source

```
# Clone repository from github
git clone https://github.com/tamminenlab/npysearch.git

# Install package using pip
pip install ./npysearch
```

## Examples

```python
# Import npysearch-win package (installed as 'npysearch')
import npysearch as npy

# Read query file into a dictionary
query = npy.read_fasta("npysearch/data/query.fasta")

# Read database file into a dictionary
database = npy.read_fasta("npysearch/data/db.fasta")

# BLAST the query against the database
results_dna = npy.blast(query, database)

# BLAST protein sequence file against itself using filenames as blast function arguments
results_prot = npy.blast(query    = "npysearch/data/prot.fasta",
                         database = "npysearch/data/prot.fasta",
                         alphabet = "protein")
```

## Caveats

* The `blast` function automatically detects whether the query and database arguments were passed as string paths to fasta files or as dictionaries of sequences. Both of them need not be input as the same type.
* Use `help(npy)` (assuming you've imported npysearch as npy) to get a list of the functions included and their docstrings. For docstrings of specific functions, for example blast, use `help(npy.blast)`

## Supported platforms

| Platform     | Python versions | Source                   |
|--------------|-----------------|--------------------------|
| win\_64      | 3.10 – 3.14     | this fork (npysearch-win) |
| linux\_64    | >= 3.7          | original npysearch        |
| osx\_64      | >= 3.7          | original npysearch        |

Details for the original package: https://anaconda.org/conda-forge/npysearch/files

## License

BSD — same as the original npysearch project.
