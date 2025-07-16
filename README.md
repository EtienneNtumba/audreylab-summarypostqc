# AudreyLab-SummaryPostQC

[![PyPI version](https://badge.fury.io/py/audreylab-summarypostqc.svg)](https://pypi.org/project/audreylab-summarypostqc/)
[![License](https://img.shields.io/github/license/EtienneNtumba/audreylab-summarypostqc)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.7%2B-blue.svg)](https://www.python.org/)

**AudreyLab-SummaryPostQC** is a robust and lightweight Python command-line utility for visualizing and annotating genome-wide association study (GWAS) summary statistics. It provides clear, publication-ready **QQ plots**, **Manhattan plots**, and supports **SNP annotation** through BioMart and MyVariant.info. It also computes the **genomic inflation factor (λGC)** as a quality control metric.

> Developed by **Etienne Kabongo**, member of the [Audrey Grant Lab](https://www.mcgill.ca/genepi/), McGill University.
> Source code: [github.com/EtienneNtumba/audreylab-summarypostqc](https://github.com/EtienneNtumba/audreylab-summarypostqc)

---

## 🧬 Use Case

This tool is particularly useful for:
- Post-QC visualization of GWAS results (e.g., after using REGENIE or PLINK)
- Detecting inflation or stratification using λGC
- Discovering signals through Manhattan plots
- Annotating significant SNPs with gene, consequence, and clinical data

---

## 🔧 Features

- ✅ Parses post-QC GWAS summary files (TSV/CSV)
- ✅ Filters out invalid or missing P-values
- ✅ Calculates genomic inflation factor (λGC)
- ✅ Generates high-resolution QQ plots
- ✅ Generates Manhattan plots by chromosome
- ✅ Annotates significant SNPs using Ensembl BioMart and MyVariant.info
- ✅ Supports custom output names and thresholds

---

## 📦 Installation

Install from [PyPI](https://pypi.org/project/audreylab-summarypostqc/) with:

```bash
pip install audreylab-summarypostqc
```

---

## 🚀 Usage

### Basic QQ + Manhattan Plot

```bash
audreylab-summarypostqc --input gwas_summary.txt --out plots
```

This generates:
- `results/plots_qqplot.png`
- `results/plots_manhattan.png`

### Custom Output Paths

```bash
audreylab-summarypostqc \
  --input gwas_summary.txt \
  --qqplot name1.png \
  --manhattan name2.png
```

### 🧬 Annotate Significant SNPs

```bash
audreylab-summarypostqc \
  --input gwas_summary.txt \
  --annotate \
  --pval-threshold 5e-6
```

This will:
- Filter SNPs with Pval < 5e-6
- Annotate them via Ensembl BioMart + MyVariant.info
- Save output to `annotated_snps.csv`

---

## ⚙️ Command-line Options

| Flag             | Description                                                                  |
|------------------|------------------------------------------------------------------------------|
| `--input`        | **[Required]** Path to the GWAS summary stats file (.tsv or .csv format)     |
| `--out`          | Prefix for output plots (e.g. `myplot`)                              |
| `--qqplot`       | Custom path for QQ plot (e.g. `qq.png`)                              |
| `--manhattan`    | Custom path for Manhattan plot (e.g. `manhattan.png`)                |
| `--annotate`     | Output file (.csv) to save annotated SNPs                                    |
| `--pval-threshold` | P-value threshold for selecting SNPs to annotate (default: `5e-2`)         |

---

## 📈 Input File Format

Your input file should be a **tab-separated** (`.tsv` or `.txt`) file with the following required columns:

| Column | Description                          |
|--------|--------------------------------------|
| Chr    | Chromosome number (1–22)             |
| Pos    | Base pair position                   |
| Pval   | P-value of association               |
| Name   | Variant rsID (used for annotation)   |
| Ref    | Reference allele                     |
| Alt    | Alternative allele                   |

⚠️ Missing or invalid values will be automatically excluded.

---

## 🧪 Output

- 📊 **QQ Plot**: Observed vs. expected -log10(P), includes λGC
- 🗺️ **Manhattan Plot**: Genome-wide P-values, with red line at 5e-8
- 🧬 **Annotation CSV (optional)**: Adds gene, consequence, clinical significance, and CADD scores

---

## 👨‍🔬 Author

**Etienne Kabongo**  
Research Assistant – Audrey Grant Lab  
McGill University – Department of Human Genetics  
📍 GitHub: [@EtienneNtumba](https://github.com/EtienneNtumba)

---

## 🤝 Contributions

Contributions, issues, and suggestions are warmly welcome!  
Feel free to open issues or pull requests on GitHub:

👉 [github.com/EtienneNtumba/audreylab-summarypostqc](https://github.com/EtienneNtumba/audreylab-summarypostqc)

---

## 📄 License

This project is released under the MIT License.  
See [LICENSE](LICENSE) for details.
