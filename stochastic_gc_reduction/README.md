# Bioinformatics and Analytical Python Tools

Practical Python notebooks and scripts developed from real computational biology, molecular biology, and analytical science workflows.

This repository collects small, focused tools for biological sequence handling, gene block design, chromatogram processing, peak picking, baseline correction, and scientific plotting. The aim is not to build a large software package, but to document useful research utilities in a readable and reproducible way.

## Current tools

### Randomised GC Content Reducer for Gene Block Synthesis

Notebook:

```text
geneblock_GC_content_reducer.ipynb
```

This notebook contains a Python function for reducing the GC content of coding DNA sequences through randomised synonymous codon replacement.

The tool was originally developed for work with high-GC actinomycete-derived genes, where commercial gene block synthesis can become difficult or fail because of excessive GC content and local sequence complexity.

The function:

- accepts a coding DNA sequence in 5' to 3' orientation
- translates the sequence using the standard genetic code
- reverse-translates the protein sequence using randomised synonymous codon selection
- preserves the encoded protein sequence
- calculates initial and final GC content
- checks whether the protein sequence is conserved after recoding
- plots global GC content before and after recoding
- plots local GC content using fixed-size sequence windows
- optionally saves results as CSV and PNG files

## Method note

The current implementation performs randomised synonymous codon selection at each amino acid position. This avoids selecting one fixed synonymous codon per amino acid globally, which could create excessive codon repetition across the sequence.

The method is intended as a practical sequence-design aid for reducing GC content while maintaining codon-level stochasticity. It is not intended to be a full codon-optimisation platform.

## Example use case

The included example applies the function to a high-GC Hygromycin-related coding sequence.

The workflow reports:

- sequence identifier
- GC-content-reduced DNA sequence
- translated protein sequence
- initial GC content
- final GC content
- GC reduction
- protein conservation status
- global GC comparison plot
- local GC window plot

## Limitations

The current version has some intentional limitations:

- synonymous codon choice is randomised and does not yet use organism-specific codon usage frequencies
- GC reduction is stochastic, so repeated runs may generate different sequences
- the tool does not yet screen for all synthesis-relevant features, such as restriction sites, homopolymer runs, repeated sequence motifs, secondary-structure-prone regions, or vendor-specific synthesis constraints
- the workflow is currently notebook-based and intended for exploratory scientific use

## Requirements

The notebook uses standard scientific Python libraries:

```python
random
pathlib
matplotlib
pandas
tqdm
```

Install dependencies with:

```bash
pip install pandas matplotlib tqdm
```

or, if using conda:

```bash
conda install pandas matplotlib tqdm
```

## Repository scope

This repository is intended to grow gradually as a collection of practical tools from computational biology and analytical workflows.

Planned or related tools may include:

- HPLC chromatogram baseline correction
- HPLC peak picking
- chromatogram plotting utilities
- small sequence-analysis helpers
- molecular biology quality-control scripts

## Author

Dr Fabio H. S. Rodrigues  
Translational ML Scientist, Life Sciences

## Licence

This project is licensed under the MIT License. See the `LICENSE` file for details.
