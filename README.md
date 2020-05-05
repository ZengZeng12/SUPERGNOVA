# SUPERGNOVA

SUPERGNOVA (SUPER GeNetic cOVariance Analyzer) is a statistical framework to perform local genetic covariance analysis. SUPERGNOVA only needs GWAS summary data and a reference panel as input data. The preprint is available at biorxiv.

## Requirements

The software is developed and tested in Linux and Mac OS environments. The following softwares and packages are required:

1. **Python 2.7**
2. **numpy**
3. **scipy**
4. **pandas**
5. **sklearn**
6. **bitarray**

## Tutorial

Suppose you would like to calculate local genetic covariance between  Crohn's disease and ulcerative colitis. We'll need a few types of files:

- **Summary statistics files:** You can get your own GWAS summary statistics files for these two diseases [here](https://www.ibdgenetics.org). We assume that the files are in the standard format that ``ldsc`` understands. If not, make sure to run them through the included ``munge_sumstats.py`` file or use the one included in ``ldsc`` (see [here](https://github.com/bulik/ldsc/wiki/Heritability-and-Genetic-Correlation#reformatting-summary-statistics) for instructions).

- **Plink bfiles:** These are files .bed/.bim/.fam format. You can download some that we have prepared for you here. These files are from the 1000 Genomes Project, with rare variants (MAF < 5\%) filtered out.

- **Genome partition files**: These files should be in bed format, one for each chromosome. Please note that different population may have different genome partition. Here is an example dataset for European population.

More details about these supplied files can be found in here.

We may run the following command:

```
python2 supergnova.py data/CD.sumstats.gz data/UC.sumstats.gz \
--N1 27726 \
--N2 28738 \
--bfile data/bfiles/eur_chr@_SNPmaf5 \
--partition data/partition/eur_chr@.bed \
--out results.txt
```
## Credits

Those using the SUPERGNOVA software should cite: Zhang, Y.L. et al. Local genetic correlation analysis reveals heterogeneous etiologic sharing of complex traits. 2020.

The LD score calculation  and the estimation of phenotypic covariance are adapted from `ldsc.py` in  `ldsc` and `ldsc_thin.py` in `GNOVA`. See [Bulik-Sullivan, B. et al. An Atlas of Genetic Correlations across Human Diseases and Traits. Nature Genetics, 2015.](https://www.nature.com/articles/ng.3406) and [Lu, Q.S. et al. A powerful approach to estimating annotation-stratified genetic covariance using GWAS summary statistics. The American Journal of Human Genetics, 2017.](https://www.cell.com/ajhg/fulltext/S0002-9297(17)30453-6)
