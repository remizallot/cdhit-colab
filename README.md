# CD-HIT in Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/remizallot/cdhit-colab/blob/main/CD-HIT_Colab.ipynb)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23503573.svg)](https://doi.org/10.5281/zenodo.23503573)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Run **CD-HIT** in the browser, with no local installation.

[CD-HIT](https://github.com/weizhongli/cdhit) clusters biological sequences and removes
redundancy. Its **web server has been unavailable since 2022**, which left users without
an install-free route to the program. This notebook builds CD-HIT from source in a Google
Colab runtime and runs it on your own sequences.

## Use it

Click the badge above. Then run the cells in order:

1. **Install CD-HIT** — downloads and compiles the version you specify (default V4.8.1).
2. **Provide your FASTA** — upload a file, or point at a path in your Google Drive.
3. **Set parameters and run** — all options are form fields with explanatory notes.
4. **Summary and provenance** — cluster counts, and a `provenance.txt` record.
5. **Download** — a zip containing the representatives, the `.clstr` file and the
   provenance record.

Nothing needs to be installed locally, and nothing outside `/content/cdhit_run` is touched.

## Why the parameters matter

Two CD-HIT options are routinely confused, and getting them wrong changes the result
without any error message:

| Flag | What it actually does |
|---|---|
| `-s` | **Minimum length ratio.** The shorter sequence must be *at least* this fraction of the representative's length. `-s 0.8` means "at least 80% as long". It is a minimum, not a maximum difference. |
| `-aS` | **Alignment coverage of the shorter sequence.** This is usually what people mean by "X% coverage". |

To cluster "at 90% identity over at least 80% of the sequence", set `-c 0.9` and
`-aS 0.8` — not `-s 0.2`.

Other options exposed:

| Flag | Meaning |
|---|---|
| `-c` | Sequence identity threshold |
| `-n` | Word length; chosen automatically from `-c` if left at 0 |
| `-aL` | Alignment coverage of the longer sequence |
| `-g 1` | Compare against all representatives and take the best match, not the first |
| `-d 0` | Keep full sequence names in the `.clstr` file |

## Reproducibility

Parameters are Colab form fields, so they are stored *in the notebook*. A saved copy is a
record of exactly what was run — unlike interactive prompts, whose values survive only in
console output.

Each run also writes `provenance.txt` with the CD-HIT version, the complete command line,
the input filename and its MD5 checksum, the sequence count, and a UTC timestamp. Keep it
with your results; it is what lets someone else reproduce the clustering.

## Citing

Please cite **CD-HIT** and, if the notebook was useful, this repository:

> Li W, Godzik A. Cd-hit: a fast program for clustering and comparing large sets of protein
> or nucleotide sequences. *Bioinformatics* **22**, 1658–1659 (2006).
> doi:10.1093/bioinformatics/btl158

> Fu L, Niu B, Zhu Z, Wu S, Li W. CD-HIT: accelerated for clustering the next-generation
> sequencing data. *Bioinformatics* **28**, 3150–3152 (2012).
> doi:10.1093/bioinformatics/bts565

This notebook is archived on Zenodo:

> Zallot R. *CD-HIT in Google Colab.* Zenodo. doi:[10.5281/zenodo.23503573](https://doi.org/10.5281/zenodo.23503573)

That is the concept DOI and always resolves to the most recent version. To cite a specific
release, use its own DOI — v1.0.0 is
[10.5281/zenodo.23503574](https://doi.org/10.5281/zenodo.23503574).

Citation metadata for this notebook is in [`CITATION.cff`](CITATION.cff).

## Licence

The notebook is released under the [MIT licence](LICENSE).

CD-HIT itself is distributed under the **GPL-2.0** licence and is **downloaded, not
redistributed**, by this notebook. See the
[CD-HIT repository](https://github.com/weizhongli/cdhit) for its terms.
