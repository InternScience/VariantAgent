# Total cholesterol demo — Sakaue et al. (2021)

## Background

This demo uses total cholesterol (TC) GWAS summary statistics from the East Asian study by
Sakaue et al. (2021, *Nature Genetics*), available through GWAS Catalog accession
[GCST90018754](https://www.ebi.ac.uk/gwas/studies/GCST90018754). The original summary statistics
are provided on GRCh37/hg19; variants retained for downstream interpretation were harmonized to
GRCh38/hg38.

Download the original summary statistics from the
[NHGRI-EBI GWAS Catalog](https://ftp.ebi.ac.uk/pub/databases/gwas/summary_statistics/GCST90018001-GCST90019000/GCST90018754/GCST90018754_buildGRCh37.tsv.gz):

```bash
mkdir -p input
wget -O input/GCST90018754_buildGRCh37.tsv.gz \
  https://ftp.ebi.ac.uk/pub/databases/gwas/summary_statistics/GCST90018001-GCST90019000/GCST90018754/GCST90018754_buildGRCh37.tsv.gz
```

## Analysis flow

1. **GWAS input** — The downloaded `input/GCST90018754_buildGRCh37.tsv.gz` file provides the
   original variant-level association statistics.
2. **Post-GWAS analysis** — VariantAgent applies fine-mapping and downstream functional modules
   to connect associated variants with genes, cellular context, molecular function,
   perturbation evidence, pathogenicity evidence, and therapeutic evidence.
3. **Variant-centred evidence** — [`evidence_report/`](evidence_report/) contains 121 standardized
   JSON evidence units, one for each retained variant, with module results and provenance kept
   together.
4. **Evidence synthesis** —
   [`report/mechanism_report.md`](report/mechanism_report.md) integrates those evidence units into
   ranked variant-gene-mechanism interpretations while retaining quality-control findings and
   unresolved evidence gaps.
