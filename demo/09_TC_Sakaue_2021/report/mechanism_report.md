# Post-GWAS variant-gene-mechanism report

Report status: **READY FOR INTERPRETATION WITH LOCAL QC QUARANTINE**.

The input variants are treated as the accepted high-confidence set; this report does not re-adjudicate fine-mapping selection.

## Coverage and provenance

- Variants retained: 121; variant-gene rows: 150.
- Local quality gate: pass_with_local_blockers; run ID: 0a8838b237f027b37b75e185.
- M2-supported variants: 55; M2-absent variants: 66. M2 absence is normal and lowers gene-link tier.
- Gene-link tiers: {'M2_SUPPORTED': 55, 'EXPLORATORY_LINK': 68, 'NO_SUPPORTED_LINK': 27}.
- External knownness: {'CONTEXT_ONLY': 53, 'EXTERNAL_GENE_MISMATCH': 1, 'NOT_QUERIED': 90, 'CANDIDATE_DATABASE_UNREPORTED': 5, 'KNOWN_ASSOCIATION': 1}.
- External-validation batch: 60 candidates queried; 90 remaining pairs are deferred (NOT_QUERIED), not classified as database-unreported.
- External schema errors: 0; candidates with supplied external rows: 60; external-only gene suggestions: 130.
- Local QC quarantine examples: 3; affected candidates are retained in audit files but excluded from finalized interpretation sections when listed by variant-scoped blocker examples.

### Quality findings

- **blocker / CODING_CONSEQUENCE_ROUTE_CONFLICT**: Coding consequences, including synonymous variants, must use the coding M7 route. (n=3; examples=rs2302134, rs738409, rs738408)
- **warning / GENE_SYMBOL_IS_ENSEMBL_ID**: A candidate-generating gene_symbol field contains a literal Ensembl identifier (ID leaked into the symbol column, e.g. a copied M2 row). The source is rejected and any independent gene-resolved source (M4/SnpEff) is retained for ranking. (n=21; examples=rs12572599:M2=ENSG00000288938:gene_symbol_is_ensembl_id, rs12572599:M4_SpliceAI=ENSG00000288938:gene_symbol_is_ensembl_id, rs57594838:M2=ENSG00000288938:gene_symbol_is_ensembl_id, rs57594838:M4_SpliceAI=ENSG00000288938:gene_symbol_is_ensembl_id, rs72819629:M4_SpliceAI=ENSG00000288938:gene_symbol_is_ensembl_id, rs7298751:M4_SpliceAI=ENSG00000294609:gene_symbol_is_ensembl_id, rs61323863:M4_SpliceAI=ENSG00000232451:gene_symbol_is_ensembl_id, rs150845180:M4_SpliceAI=ENSG00000232451:gene_symbol_is_ensembl_id, rs62123784:M4_SpliceAI=ENSG00000232451:gene_symbol_is_ensembl_id, rs12712884:M4_SpliceAI=ENSG00000302183:gene_symbol_is_ensembl_id)
- **warning / GENE_SYMBOL_IS_GENBANK_ACCESSION**: A candidate-generating gene_symbol field contains a GenBank/RefSeq accession with a version suffix (e.g. AF131215.9), the signature of a copied M2 row stamped across variants/chromosomes. The source is rejected and any independent gene-resolved source (M4/SnpEff) is retained for ranking. (n=12; examples=rs148608463:M5_SnpEff=AC079602.1:gene_symbol_is_genbank_accession, rs62124995:M5_SnpEff=AC092594.1:gene_symbol_is_genbank_accession, rs7596281:M5_SnpEff=AC092594.1:gene_symbol_is_genbank_accession, rs12463657:M5_SnpEff=AC092594.1:gene_symbol_is_genbank_accession, rs61323863:M5_SnpEff=AC016768.1:gene_symbol_is_genbank_accession, rs150845180:M5_SnpEff=AC016768.1:gene_symbol_is_genbank_accession, rs62123784:M5_SnpEff=AC016768.1:gene_symbol_is_genbank_accession, rs6543790:M5_SnpEff=AC009499.1:gene_symbol_is_genbank_accession, rs11900922:M5_SnpEff=AC009499.1:gene_symbol_is_genbank_accession, rs62132790:M5_SnpEff=AC009499.1:gene_symbol_is_genbank_accession)
- **warning / UPSTREAM_MANIFEST_ABSENT**: No upstream schema/run manifest was found; this run will create an input hash manifest. (n=1; examples=)

## Part I. Variant-gene-mechanism ranking

### M2-supported pairs

| Variant rank | Pair rank | Variant | Gene | Tier | Local mechanism | Knownness | Flags |
|---:|---:|---|---|---|---|---|---|
| 1 | 1 | rs2495477 | PCSK9 | M2_SUPPORTED | PCSK9 has local gene-link support from ABF, FINEMAP, MAGMA; SnpEff annotates rs2495477 as splice_region_variant&intron_variant at PCSK9. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 2 | 2 | rs12136600 | PCSK9 | M2_SUPPORTED | PCSK9 has local gene-link support from ABF, FINEMAP, MAGMA; SnpEff annotates rs12136600 as downstream_gene_variant at PCSK9. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 3 | 3 | rs1313566 | GCKR | M2_SUPPORTED | GCKR has local gene-link support from FINEMAP, MAGMA; SnpEff annotates rs1313566 as downstream_gene_variant at GCKR. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 4 | 4 | rs2911711 | GCKR | M2_SUPPORTED | GCKR has local gene-link support from FINEMAP, MAGMA; SnpEff annotates rs2911711 as downstream_gene_variant at GCKR. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 5 | 5 | rs9958734 | LIPG | M2_SUPPORTED | LIPG has local gene-link support from ABF, SuSiE, MAGMA; SnpEff annotates rs9958734 as 3_prime_UTR_variant at LIPG. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 6 | 6 | rs67053123 | SCARB1 | M2_SUPPORTED | SCARB1 has local gene-link support from ABF, FINEMAP, MAGMA; SnpEff annotates rs67053123 as intron_variant at SCARB1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 7 | 7 | rs11082764 | LIPG | M2_SUPPORTED | LIPG has local gene-link support from ABF, SuSiE, MAGMA; SnpEff annotates rs11082764 as downstream_gene_variant at LIPG. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 8 | 8 | rs3786247 | LIPG | M2_SUPPORTED | LIPG has local gene-link support from ABF, SuSiE, MAGMA; SnpEff annotates rs3786247 as 3_prime_UTR_variant at LIPG. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 9 | 9 | rs1260333 | GCKR | M2_SUPPORTED | GCKR has local gene-link support from FINEMAP, MAGMA; SnpEff annotates rs1260333 as downstream_gene_variant at GCKR. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 10 | 10 | rs1883025 | ABCA1 | M2_SUPPORTED | ABCA1 has local gene-link support from SuSiE, MAGMA; SnpEff annotates rs1883025 as intron_variant at ABCA1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 11 | 11 | rs4704210 | HMGCR | M2_SUPPORTED | HMGCR has local gene-link support from ABF, FINEMAP, MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 12 | 12 | rs611917 | CELSR2 | M2_SUPPORTED | CELSR2 has local gene-link support from MAGMA; SnpEff annotates rs611917 as intron_variant at CELSR2; SpliceAI predicts a CELSR2 splice effect (DSmax=0.02). | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 13 | 13 | rs12412743 | TECTB | M2_SUPPORTED | TECTB has local gene-link support from MAGMA; SnpEff annotates rs12412743 as intron_variant at TECTB; SpliceAI predicts a TECTB splice effect (DSmax=0.02). | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 14 | 14 | rs2070895 | LIPC | M2_SUPPORTED | LIPC has local gene-link support from MAGMA; SnpEff annotates rs2070895 as upstream_gene_variant at LIPC. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 15 | 15 | rs10889356 | DOCK7 | M2_SUPPORTED | DOCK7 has local gene-link support from MAGMA; SnpEff annotates rs10889356 as upstream_gene_variant at DOCK7. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 16 | 16 | rs11096676 | HS1BP3 | M2_SUPPORTED | HS1BP3 has local gene-link support from MAGMA; SnpEff annotates rs11096676 as intron_variant at HS1BP3. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 17 | 17 | rs73596816 | LPA | M2_SUPPORTED | LPA has local gene-link support from FINEMAP; SnpEff annotates rs73596816 as intron_variant at LPA. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 18 | 18 | rs10493322 | USP1 | M2_SUPPORTED | USP1 has local gene-link support from MAGMA; SnpEff annotates rs10493322 as intron_variant at USP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 19 | 19 | rs10158897 | USP1 | M2_SUPPORTED | USP1 has local gene-link support from MAGMA; SnpEff annotates rs10158897 as downstream_gene_variant at USP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 20 | 20 | rs11207970 | DOCK7 | M2_SUPPORTED | DOCK7 has local gene-link support from MAGMA; SnpEff annotates rs11207970 as downstream_gene_variant at DOCK7. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 21 | 21 | rs3913007 | DOCK7 | M2_SUPPORTED | DOCK7 has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 22 | 22 | rs12721025 | APOA1 | M2_SUPPORTED | APOA1 has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 23 | 23 | rs660240 | CELSR2 | M2_SUPPORTED | CELSR2 has local gene-link support from MAGMA; SnpEff annotates rs660240 as 3_prime_UTR_variant at CELSR2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 24 | 24 | rs4970834 | CELSR2 | M2_SUPPORTED | CELSR2 has local gene-link support from MAGMA; SnpEff annotates rs4970834 as intron_variant at CELSR2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 25 | 25 | rs148608463 | HNF1A | M2_SUPPORTED | HNF1A has local gene-link support from SuSiE, MAGMA. | EXTERNAL_GENE_MISMATCH | multiple_gene_assignments, invalid_gene_source_rejected |
| 26 | 26 | rs99780 | FADS2 | M2_SUPPORTED | FADS2 has local gene-link support from MAGMA; SnpEff annotates rs99780 as downstream_gene_variant at FADS2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 27 | 27 | rs28456 | FADS1 | M2_SUPPORTED | FADS1 has local gene-link support from MAGMA; SnpEff annotates rs28456 as upstream_gene_variant at FADS1. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 28 | 28 | rs3902354 | CELSR2 | M2_SUPPORTED | CELSR2 has local gene-link support from MAGMA; SnpEff annotates rs3902354 as downstream_gene_variant at CELSR2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 29 | 29 | rs174592 | FADS2 | M2_SUPPORTED | FADS2 has local gene-link support from MAGMA; SnpEff annotates rs174592 as upstream_gene_variant at FADS2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 30 | 30 | rs174574 | FADS1 | M2_SUPPORTED | FADS1 has local gene-link support from MAGMA; SnpEff annotates rs174574 as upstream_gene_variant at FADS1. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 31 | 31 | rs174576 | FADS2 | M2_SUPPORTED | FADS2 has local gene-link support from MAGMA; SnpEff annotates rs174576 as upstream_gene_variant at FADS2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 32 | 32 | rs72819629 | TECTB | M2_SUPPORTED | TECTB has local gene-link support from MAGMA; SnpEff annotates rs72819629 as upstream_gene_variant at TECTB. | CONTEXT_ONLY | invalid_gene_source_rejected, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 33 | 33 | rs1168114 | DOCK7 | M2_SUPPORTED | DOCK7 has local gene-link support from MAGMA; SnpEff annotates rs1168114 as upstream_gene_variant at DOCK7. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 34 | 34 | rs738408 | PNPLA3 | M2_SUPPORTED | PNPLA3 has local gene-link support from MAGMA; rs738408 has protein-level evidence for PNPLA3 (synonymous_variant); SpliceAI predicts a PNPLA3 splice effect (DSmax=0.01). | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 35 | 35 | rs738409 | PNPLA3 | M2_SUPPORTED | PNPLA3 has local gene-link support from MAGMA; rs738409 has protein-level evidence for PNPLA3 (missense_variant). | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 36 | 36 | rs11748027 | POLK | M2_SUPPORTED | POLK has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 37 | 37 | rs2519093 | ABO | M2_SUPPORTED | ABO has local gene-link support from MAGMA; SnpEff annotates rs2519093 as intron_variant at ABO. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 38 | 38 | rs550057 | ABO | M2_SUPPORTED | ABO has local gene-link support from MAGMA; SnpEff annotates rs550057 as intron_variant at ABO. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 39 | 39 | rs360799 | EHBP1 | M2_SUPPORTED | EHBP1 has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 40 | 40 | rs3751674 | ZFPM1 | M2_SUPPORTED | ZFPM1 has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 41 | 41 | rs6129786 | ZHX3 | M2_SUPPORTED | ZHX3 has local gene-link support from MAGMA; SnpEff annotates rs6129786 as intron_variant at ZHX3. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 42 | 42 | rs4461246 | EHBP1 | M2_SUPPORTED | EHBP1 has local gene-link support from MAGMA; SnpEff annotates rs4461246 as intron_variant at EHBP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 43 | 43 | rs7220935 | NPEPPS | M2_SUPPORTED | NPEPPS has local gene-link support from MAGMA; SnpEff annotates rs7220935 as downstream_gene_variant at NPEPPS. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 44 | 44 | rs8072100 | NPEPPS | M2_SUPPORTED | NPEPPS has local gene-link support from MAGMA; SnpEff annotates rs8072100 as upstream_gene_variant at NPEPPS. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 45 | 45 | rs6129785 | ZHX3 | M2_SUPPORTED | ZHX3 has local gene-link support from MAGMA; SnpEff annotates rs6129785 as intron_variant at ZHX3. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 46 | 46 | rs12935117 | ZFPM1 | M2_SUPPORTED | ZFPM1 has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 47 | 47 | rs6129750 | TOP1 | M2_SUPPORTED | TOP1 has local gene-link support from MAGMA; SnpEff annotates rs6129750 as intron_variant at TOP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 48 | 48 | rs56373728 | EHBP1 | M2_SUPPORTED | EHBP1 has local gene-link support from MAGMA; SnpEff annotates rs56373728 as upstream_gene_variant at EHBP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 49 | 49 | rs10168771 | EHBP1 | M2_SUPPORTED | EHBP1 has local gene-link support from MAGMA; SnpEff annotates rs10168771 as intron_variant at EHBP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 50 | 50 | rs2710644 | EHBP1 | M2_SUPPORTED | EHBP1 has local gene-link support from MAGMA; SnpEff annotates rs2710644 as intron_variant at EHBP1. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 51 | 51 | rs2302134 | ABCA6 | M2_SUPPORTED | ABCA6 has local gene-link support from integrated V2G; rs2302134 has protein-level evidence for ABCA6 (missense_variant); SpliceAI predicts a ABCA6 splice effect (DSmax=0.02). | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |

### No-M2 functional rescue

No candidates in this section.

### Exploratory links

| Variant rank | Pair rank | Variant | Gene | Tier | Local mechanism | Knownness | Flags |
|---:|---:|---|---|---|---|---|---|
| 69 | 73 | rs62132790 | LINC01320 | EXPLORATORY_LINK | Gene-resolved annotation nominates LINC01320; no downstream molecular mechanism is established locally. | CANDIDATE_DATABASE_UNREPORTED | invalid_gene_source_rejected |
| 25 | 93 | rs148608463 | HNF1A-AS1 | EXPLORATORY_LINK | Gene-resolved annotation nominates HNF1A-AS1; no downstream molecular mechanism is established locally. | KNOWN_ASSOCIATION | multiple_gene_assignments, invalid_gene_source_rejected |
| 82 | 102 | rs11749783 | CTD-2235C13.2 | EXPLORATORY_LINK | SnpEff annotates rs11749783 as intron_variant at CTD-2235C13.2. | CONTEXT_ONLY | invalid_gene_source_rejected, M7_is_derived_not_independent |
| 83 | 103 | rs7596281 | LINC01376 | EXPLORATORY_LINK | Gene-resolved annotation nominates LINC01376; no downstream molecular mechanism is established locally. | CONTEXT_ONLY | invalid_gene_source_rejected |
| 85 | 111 | rs11900922 | LINC01320 | EXPLORATORY_LINK | Gene-resolved annotation nominates LINC01320; no downstream molecular mechanism is established locally. | CANDIDATE_DATABASE_UNREPORTED | invalid_gene_source_rejected |
| 87 | 114 | rs6543790 | LINC01320 | EXPLORATORY_LINK | Gene-resolved annotation nominates LINC01320; no downstream molecular mechanism is established locally. | CANDIDATE_DATABASE_UNREPORTED | invalid_gene_source_rejected |
| 88 | 115 | rs12469022 | LINC01320 | EXPLORATORY_LINK | Gene-resolved annotation nominates LINC01320; no downstream molecular mechanism is established locally. | CANDIDATE_DATABASE_UNREPORTED | invalid_gene_source_rejected |
| 91 | 119 | rs12463657 | LINC01376 | EXPLORATORY_LINK | Gene-resolved annotation nominates LINC01376; no downstream molecular mechanism is established locally. | CONTEXT_ONLY | invalid_gene_source_rejected |
| 93 | 122 | rs62124995 | LINC01376 | EXPLORATORY_LINK | Gene-resolved annotation nominates LINC01376; no downstream molecular mechanism is established locally. | CANDIDATE_DATABASE_UNREPORTED | invalid_gene_source_rejected |

### No supported gene link

No candidates in this section.

## Part II. Known variant-gene mechanisms and associations

### rs148608463–HNF1A-AS1: KNOWN_ASSOCIATION

Local chain: Gene-resolved annotation nominates HNF1A-AS1; no downstream molecular mechanism is established locally.

Evidence grade: association/prioritization only — no exact mechanistic (functional) literature was retrieved.

External basis:

- [gwas_catalog GWASCatalog:64400845](https://www.ebi.ac.uk/gwas/variants/rs148608463): GWAS Catalog association row retrieved for the variant: trait=Plateletcrit; mapped_genes=HNF1A-AS1; p=5e-29. (scope=exact_variant_gene_trait; type=association; support=supports).

Context and unsupported steps:

- [gwas_catalog GWASCatalog:188095116](https://www.ebi.ac.uk/gwas/variants/rs148608463): GWAS Catalog association row retrieved for the variant: trait=Platelet crit (UKB data field 30090); mapped_genes=HNF1A-AS1; p=1e-32. (scope=exact_variant_gene; type=association; support=context).
- [gwas_catalog GWASCatalog:106265368](https://www.ebi.ac.uk/gwas/variants/rs148608463): GWAS Catalog association row retrieved for the variant: trait=Multi-trait sum score; mapped_genes=HNF1A-AS1; p=7e-12. (scope=exact_variant_gene; type=association; support=context).
- [gwas_catalog GWASCatalog:98279317](https://www.ebi.ac.uk/gwas/variants/rs148608463): GWAS Catalog association row retrieved for the variant: trait=Coronary artery disease or fibrinogen levels (pleiotropy); mapped_genes=HNF1A-AS1; p=2e-12. (scope=exact_variant_gene; type=association; support=context).
- [gwas_catalog GWASCatalog:98278808](https://www.ebi.ac.uk/gwas/variants/rs148608463): GWAS Catalog association row retrieved for the variant: trait=Coronary artery disease or factor XI levels (pleiotropy); mapped_genes=HNF1A-AS1; p=3e-12. (scope=exact_variant_gene; type=association; support=context).
- [gwas_catalog GWASCatalog:98278379](https://www.ebi.ac.uk/gwas/variants/rs148608463): GWAS Catalog association row retrieved for the variant: trait=Coronary artery disease or von Willebrand factor levels (pleiotropy); mapped_genes=HNF1A-AS1; p=3e-12. (scope=exact_variant_gene; type=association; support=context).
- [gwas_catalog GWASCatalog:98277955](https://www.ebi.ac.uk/gwas/variants/rs148608463): GWAS Catalog association row retrieved for the variant: trait=Coronary artery disease or factor VIII levels (pleiotropy); mapped_genes=HNF1A-AS1; p=3e-12. (scope=exact_variant_gene; type=association; support=context).
- [gwas_catalog GWASCatalog:98277511](https://www.ebi.ac.uk/gwas/variants/rs148608463): GWAS Catalog association row retrieved for the variant: trait=Coronary artery disease or factor VII levels (pleiotropy); mapped_genes=HNF1A-AS1; p=3e-12. (scope=exact_variant_gene; type=association; support=context).
- [gwas_catalog GWASCatalog:96194495](https://www.ebi.ac.uk/gwas/variants/rs148608463): GWAS Catalog association row retrieved for the variant: trait=Sphingomyelin levels; mapped_genes=HNF1A-AS1; p=4e-09. (scope=exact_variant_gene; type=association; support=context).
- [gwas_catalog GWASCatalog:96140533](https://www.ebi.ac.uk/gwas/variants/rs148608463): GWAS Catalog association row retrieved for the variant: trait=Free cholesterol levels in IDL; mapped_genes=HNF1A-AS1; p=1e-11. (scope=exact_variant_gene; type=association; support=context).
- [open_targets OpenTargets:GCST90092880:1](https://platform.opentargets.org/variant/12_120975224_G_A): Open Targets variant credible-set context retrieved: trait=Linoleic acid levels; variant_rsids=rs148608463; gene not present in retrieved row. (scope=locus_only; type=context; support=context).
- [open_targets OpenTargets:GCST90435755:2](https://platform.opentargets.org/variant/12_120975224_G_A): Open Targets variant credible-set context retrieved: trait=Hypercholesterolemia (PheCode 272.11); variant_rsids=rs148608463; gene not present in retrieved row. (scope=locus_only; type=context; support=context).
- [open_targets OpenTargets:GCST011583:3](https://platform.opentargets.org/variant/12_120975224_G_A): Open Targets variant credible-set context retrieved: trait=Serum C-reactive protein concentration; variant_rsids=rs148608463; gene not present in retrieved row. (scope=locus_only; type=context; support=context).
- [open_targets OpenTargets:GCST90474571:4](https://platform.opentargets.org/variant/12_120975224_G_A): Open Targets variant credible-set context retrieved: trait=Reticulocyte percentage (UKB data field 30240); variant_rsids=rs148608463; gene not present in retrieved row. (scope=locus_only; type=context; support=context).
- [open_targets OpenTargets:GCST90269516:5](https://platform.opentargets.org/variant/12_120975224_G_A): Open Targets variant credible-set context retrieved: trait=Total free cholesterol levels (UKB data field 23419); variant_rsids=rs148608463; gene not present in retrieved row. (scope=locus_only; type=context; support=context).
- [open_targets OpenTargets:GCST90691932:6](https://platform.opentargets.org/variant/12_120975224_G_A): Open Targets variant credible-set context retrieved: trait=ICD10 I25: Chronic ischaemic heart disease; variant_rsids=rs148608463; gene not present in retrieved row. (scope=locus_only; type=context; support=context).
- [open_targets OpenTargets:GCST90269520:7](https://platform.opentargets.org/variant/12_120975224_G_A): Open Targets variant credible-set context retrieved: trait=Total lipids in lipoprotein particles (UKB data field 23423); variant_rsids=rs148608463; gene not present in retrieved row. (scope=locus_only; type=context; support=context).
- [open_targets OpenTargets:GCST90302134:8](https://platform.opentargets.org/variant/12_120975224_G_A): Open Targets variant credible-set context retrieved: trait=Phospholipids in very large HDL; variant_rsids=rs148608463; gene not present in retrieved row. (scope=locus_only; type=context; support=context).
- [open_targets OpenTargets:GCST90497282:9](https://platform.opentargets.org/variant/12_120975224_G_A): Open Targets variant credible-set context retrieved: trait=Glutamine levels; variant_rsids=rs148608463; gene not present in retrieved row. (scope=locus_only; type=context; support=context).
- [open_targets OpenTargets:GCST90092943:10](https://platform.opentargets.org/variant/12_120975224_G_A): Open Targets variant credible-set context retrieved: trait=Remnant cholesterol (non-HDL, non-LDL -cholesterol); variant_rsids=rs148608463; gene not present in retrieved row. (scope=locus_only; type=context; support=context).

Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

Direction gate: the report does not infer a risk-allele molecular direction unless allele harmonization is explicitly documented.


## Part III. Database-unreported, testable hypotheses

> “Database-unreported” means that the recorded PubMed, GWAS Catalog, and Open Targets searches all completed without an exact curated pair hit. It is not proof of absolute novelty.

### H1: rs62132790–LINC01320

rs62132790 may influence LINC01320 because gene-resolved annotation supplies an exploratory link. The effect allele-to-molecular-direction chain is not harmonized, so neither direction nor causality is asserted.

Testable validation: Test the proposed link by targeted enhancer perturbation and measure nearby and chromatin-contacted genes before assigning direction.

Local confidence tier: EXPLORATORY_LINK; rank reason: Only exploratory gene-resolved annotation is available.

### H2: rs11900922–LINC01320

rs11900922 may influence LINC01320 because gene-resolved annotation supplies an exploratory link. The effect allele-to-molecular-direction chain is not harmonized, so neither direction nor causality is asserted.

Testable validation: Test the proposed link by targeted enhancer perturbation and measure nearby and chromatin-contacted genes before assigning direction.

Local confidence tier: EXPLORATORY_LINK; rank reason: Only exploratory gene-resolved annotation is available.

### H3: rs6543790–LINC01320

rs6543790 may influence LINC01320 because gene-resolved annotation supplies an exploratory link. The effect allele-to-molecular-direction chain is not harmonized, so neither direction nor causality is asserted.

Testable validation: Test the proposed link by targeted enhancer perturbation and measure nearby and chromatin-contacted genes before assigning direction.

Local confidence tier: EXPLORATORY_LINK; rank reason: Only exploratory gene-resolved annotation is available.

### H4: rs12469022–LINC01320

rs12469022 may influence LINC01320 because gene-resolved annotation supplies an exploratory link. The effect allele-to-molecular-direction chain is not harmonized, so neither direction nor causality is asserted.

Testable validation: Test the proposed link by targeted enhancer perturbation and measure nearby and chromatin-contacted genes before assigning direction.

Local confidence tier: EXPLORATORY_LINK; rank reason: Only exploratory gene-resolved annotation is available.

### H5: rs62124995–LINC01376

rs62124995 may influence LINC01376 because gene-resolved annotation supplies an exploratory link. The effect allele-to-molecular-direction chain is not harmonized, so neither direction nor causality is asserted.

Testable validation: Test the proposed link by targeted enhancer perturbation and measure nearby and chromatin-contacted genes before assigning direction.

Local confidence tier: EXPLORATORY_LINK; rank reason: Only exploratory gene-resolved annotation is available.


## Local QC quarantine

The following candidates match variant-scoped blocker examples. They are retained in the audit trail but excluded from finalized known-mechanism and database-unreported hypothesis sections until their local QC findings are repaired.

| Variant rank | Pair rank | Variant | Gene | Tier | Local QC findings |
|---:|---:|---|---|---|---|
| 34 | 34 | rs738408 | PNPLA3 | M2_SUPPORTED | CODING_CONSEQUENCE_ROUTE_CONFLICT |
| 35 | 35 | rs738409 | PNPLA3 | M2_SUPPORTED | CODING_CONSEQUENCE_ROUTE_CONFLICT |
| 51 | 51 | rs2302134 | ABCA6 | M2_SUPPORTED | CODING_CONSEQUENCE_ROUTE_CONFLICT |

## External-validation unresolved queue

| Variant rank | Pair rank | Variant | Gene | Tier | Local mechanism | Knownness | Flags |
|---:|---:|---|---|---|---|---|---|
| 1 | 1 | rs2495477 | PCSK9 | M2_SUPPORTED | PCSK9 has local gene-link support from ABF, FINEMAP, MAGMA; SnpEff annotates rs2495477 as splice_region_variant&intron_variant at PCSK9. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 2 | 2 | rs12136600 | PCSK9 | M2_SUPPORTED | PCSK9 has local gene-link support from ABF, FINEMAP, MAGMA; SnpEff annotates rs12136600 as downstream_gene_variant at PCSK9. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 3 | 3 | rs1313566 | GCKR | M2_SUPPORTED | GCKR has local gene-link support from FINEMAP, MAGMA; SnpEff annotates rs1313566 as downstream_gene_variant at GCKR. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 4 | 4 | rs2911711 | GCKR | M2_SUPPORTED | GCKR has local gene-link support from FINEMAP, MAGMA; SnpEff annotates rs2911711 as downstream_gene_variant at GCKR. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 5 | 5 | rs9958734 | LIPG | M2_SUPPORTED | LIPG has local gene-link support from ABF, SuSiE, MAGMA; SnpEff annotates rs9958734 as 3_prime_UTR_variant at LIPG. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 6 | 6 | rs67053123 | SCARB1 | M2_SUPPORTED | SCARB1 has local gene-link support from ABF, FINEMAP, MAGMA; SnpEff annotates rs67053123 as intron_variant at SCARB1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 7 | 7 | rs11082764 | LIPG | M2_SUPPORTED | LIPG has local gene-link support from ABF, SuSiE, MAGMA; SnpEff annotates rs11082764 as downstream_gene_variant at LIPG. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 8 | 8 | rs3786247 | LIPG | M2_SUPPORTED | LIPG has local gene-link support from ABF, SuSiE, MAGMA; SnpEff annotates rs3786247 as 3_prime_UTR_variant at LIPG. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 9 | 9 | rs1260333 | GCKR | M2_SUPPORTED | GCKR has local gene-link support from FINEMAP, MAGMA; SnpEff annotates rs1260333 as downstream_gene_variant at GCKR. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 10 | 10 | rs1883025 | ABCA1 | M2_SUPPORTED | ABCA1 has local gene-link support from SuSiE, MAGMA; SnpEff annotates rs1883025 as intron_variant at ABCA1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 11 | 11 | rs4704210 | HMGCR | M2_SUPPORTED | HMGCR has local gene-link support from ABF, FINEMAP, MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 12 | 12 | rs611917 | CELSR2 | M2_SUPPORTED | CELSR2 has local gene-link support from MAGMA; SnpEff annotates rs611917 as intron_variant at CELSR2; SpliceAI predicts a CELSR2 splice effect (DSmax=0.02). | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 13 | 13 | rs12412743 | TECTB | M2_SUPPORTED | TECTB has local gene-link support from MAGMA; SnpEff annotates rs12412743 as intron_variant at TECTB; SpliceAI predicts a TECTB splice effect (DSmax=0.02). | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 14 | 14 | rs2070895 | LIPC | M2_SUPPORTED | LIPC has local gene-link support from MAGMA; SnpEff annotates rs2070895 as upstream_gene_variant at LIPC. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 15 | 15 | rs10889356 | DOCK7 | M2_SUPPORTED | DOCK7 has local gene-link support from MAGMA; SnpEff annotates rs10889356 as upstream_gene_variant at DOCK7. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 16 | 16 | rs11096676 | HS1BP3 | M2_SUPPORTED | HS1BP3 has local gene-link support from MAGMA; SnpEff annotates rs11096676 as intron_variant at HS1BP3. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 17 | 17 | rs73596816 | LPA | M2_SUPPORTED | LPA has local gene-link support from FINEMAP; SnpEff annotates rs73596816 as intron_variant at LPA. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 18 | 18 | rs10493322 | USP1 | M2_SUPPORTED | USP1 has local gene-link support from MAGMA; SnpEff annotates rs10493322 as intron_variant at USP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 19 | 19 | rs10158897 | USP1 | M2_SUPPORTED | USP1 has local gene-link support from MAGMA; SnpEff annotates rs10158897 as downstream_gene_variant at USP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 20 | 20 | rs11207970 | DOCK7 | M2_SUPPORTED | DOCK7 has local gene-link support from MAGMA; SnpEff annotates rs11207970 as downstream_gene_variant at DOCK7. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 21 | 21 | rs3913007 | DOCK7 | M2_SUPPORTED | DOCK7 has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 22 | 22 | rs12721025 | APOA1 | M2_SUPPORTED | APOA1 has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 23 | 23 | rs660240 | CELSR2 | M2_SUPPORTED | CELSR2 has local gene-link support from MAGMA; SnpEff annotates rs660240 as 3_prime_UTR_variant at CELSR2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 24 | 24 | rs4970834 | CELSR2 | M2_SUPPORTED | CELSR2 has local gene-link support from MAGMA; SnpEff annotates rs4970834 as intron_variant at CELSR2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 25 | 25 | rs148608463 | HNF1A | M2_SUPPORTED | HNF1A has local gene-link support from SuSiE, MAGMA. | EXTERNAL_GENE_MISMATCH | multiple_gene_assignments, invalid_gene_source_rejected |
| 26 | 26 | rs99780 | FADS2 | M2_SUPPORTED | FADS2 has local gene-link support from MAGMA; SnpEff annotates rs99780 as downstream_gene_variant at FADS2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 27 | 27 | rs28456 | FADS1 | M2_SUPPORTED | FADS1 has local gene-link support from MAGMA; SnpEff annotates rs28456 as upstream_gene_variant at FADS1. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 28 | 28 | rs3902354 | CELSR2 | M2_SUPPORTED | CELSR2 has local gene-link support from MAGMA; SnpEff annotates rs3902354 as downstream_gene_variant at CELSR2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 29 | 29 | rs174592 | FADS2 | M2_SUPPORTED | FADS2 has local gene-link support from MAGMA; SnpEff annotates rs174592 as upstream_gene_variant at FADS2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 30 | 30 | rs174574 | FADS1 | M2_SUPPORTED | FADS1 has local gene-link support from MAGMA; SnpEff annotates rs174574 as upstream_gene_variant at FADS1. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 31 | 31 | rs174576 | FADS2 | M2_SUPPORTED | FADS2 has local gene-link support from MAGMA; SnpEff annotates rs174576 as upstream_gene_variant at FADS2. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 32 | 32 | rs72819629 | TECTB | M2_SUPPORTED | TECTB has local gene-link support from MAGMA; SnpEff annotates rs72819629 as upstream_gene_variant at TECTB. | CONTEXT_ONLY | invalid_gene_source_rejected, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 33 | 33 | rs1168114 | DOCK7 | M2_SUPPORTED | DOCK7 has local gene-link support from MAGMA; SnpEff annotates rs1168114 as upstream_gene_variant at DOCK7. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 34 | 34 | rs738408 | PNPLA3 | M2_SUPPORTED | PNPLA3 has local gene-link support from MAGMA; rs738408 has protein-level evidence for PNPLA3 (synonymous_variant); SpliceAI predicts a PNPLA3 splice effect (DSmax=0.01). | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 35 | 35 | rs738409 | PNPLA3 | M2_SUPPORTED | PNPLA3 has local gene-link support from MAGMA; rs738409 has protein-level evidence for PNPLA3 (missense_variant). | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 36 | 36 | rs11748027 | POLK | M2_SUPPORTED | POLK has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 37 | 37 | rs2519093 | ABO | M2_SUPPORTED | ABO has local gene-link support from MAGMA; SnpEff annotates rs2519093 as intron_variant at ABO. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 38 | 38 | rs550057 | ABO | M2_SUPPORTED | ABO has local gene-link support from MAGMA; SnpEff annotates rs550057 as intron_variant at ABO. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 39 | 39 | rs360799 | EHBP1 | M2_SUPPORTED | EHBP1 has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 40 | 40 | rs3751674 | ZFPM1 | M2_SUPPORTED | ZFPM1 has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 41 | 41 | rs6129786 | ZHX3 | M2_SUPPORTED | ZHX3 has local gene-link support from MAGMA; SnpEff annotates rs6129786 as intron_variant at ZHX3. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 42 | 42 | rs4461246 | EHBP1 | M2_SUPPORTED | EHBP1 has local gene-link support from MAGMA; SnpEff annotates rs4461246 as intron_variant at EHBP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 43 | 43 | rs7220935 | NPEPPS | M2_SUPPORTED | NPEPPS has local gene-link support from MAGMA; SnpEff annotates rs7220935 as downstream_gene_variant at NPEPPS. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 44 | 44 | rs8072100 | NPEPPS | M2_SUPPORTED | NPEPPS has local gene-link support from MAGMA; SnpEff annotates rs8072100 as upstream_gene_variant at NPEPPS. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 45 | 45 | rs6129785 | ZHX3 | M2_SUPPORTED | ZHX3 has local gene-link support from MAGMA; SnpEff annotates rs6129785 as intron_variant at ZHX3. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 46 | 46 | rs12935117 | ZFPM1 | M2_SUPPORTED | ZFPM1 has local gene-link support from MAGMA. | CONTEXT_ONLY | multiple_gene_assignments |
| 47 | 47 | rs6129750 | TOP1 | M2_SUPPORTED | TOP1 has local gene-link support from MAGMA; SnpEff annotates rs6129750 as intron_variant at TOP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 48 | 48 | rs56373728 | EHBP1 | M2_SUPPORTED | EHBP1 has local gene-link support from MAGMA; SnpEff annotates rs56373728 as upstream_gene_variant at EHBP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 49 | 49 | rs10168771 | EHBP1 | M2_SUPPORTED | EHBP1 has local gene-link support from MAGMA; SnpEff annotates rs10168771 as intron_variant at EHBP1. | CONTEXT_ONLY | M2_gene_matches_M5_assignment, M7_is_derived_not_independent |
| 50 | 50 | rs2710644 | EHBP1 | M2_SUPPORTED | EHBP1 has local gene-link support from MAGMA; SnpEff annotates rs2710644 as intron_variant at EHBP1. | CONTEXT_ONLY | multiple_gene_assignments, M2_gene_matches_M5_assignment, M7_is_derived_not_independent |

## External-validation resolution notes

- **rs2495477–PCSK9** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs12136600–PCSK9** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs1313566–GCKR** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs2911711–GCKR** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs9958734–LIPG** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs67053123–SCARB1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs11082764–LIPG** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs3786247–LIPG** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs1260333–GCKR** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs1883025–ABCA1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs4704210–HMGCR** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs611917–CELSR2** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs12412743–TECTB** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs2070895–LIPC** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs10889356–DOCK7** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.
  - External-only gene suggestion: [DOCK7-DT](https://www.ebi.ac.uk/gwas/variants/rs10889356) — GWAS Catalog association row retrieved for the variant: trait=Triglyceride levels; mapped_genes=DOCK7-DT; p=1e-27.

- **rs11096676–HS1BP3** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs73596816–LPA** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs10493322–USP1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs10158897–USP1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs11207970–DOCK7** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.
  - External-only gene suggestion: [USP1](https://www.ebi.ac.uk/gwas/variants/rs11207970) — GWAS Catalog association row retrieved for the variant: trait=Free Cholesterol to Total Lipids in Chylomicrons and Extremely Large VLDL percentage; mapped_genes=USP1; p=2e-19.

- **rs3913007–DOCK7** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs12721025–APOA1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs660240–CELSR2** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs4970834–CELSR2** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs148608463–HNF1A** (EXTERNAL_GENE_MISMATCH):
  - Structured external record gene(s) do not match the local candidate gene: HNF1A-AS1.
  - External evidence points to a different structured gene; keep this pair unresolved and review external-only suggestions.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.
  - External-only gene suggestion: [HNF1A-AS1](https://www.ebi.ac.uk/gwas/variants/rs148608463) — GWAS Catalog association row retrieved for the variant: trait=Platelet crit (UKB data field 30090); mapped_genes=HNF1A-AS1; p=1e-32.

- **rs99780–FADS2** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs28456–FADS1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs3902354–CELSR2** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs174592–FADS2** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs174574–FADS1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.
  - External-only gene suggestion: [FADS2](https://www.ebi.ac.uk/gwas/variants/rs174574) — GWAS Catalog association row retrieved for the variant: trait=High triglyceride trajectory in type 2 diabetes; mapped_genes=FADS2; p=1e-07.

- **rs174576–FADS2** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs72819629–TECTB** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs1168114–DOCK7** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.
  - External-only gene suggestion: [DOCK7-DT](https://www.ebi.ac.uk/gwas/variants/rs1168114) — GWAS Catalog association row retrieved for the variant: trait=Phospholipids to Total Lipids in Medium HDL percentage; mapped_genes=DOCK7-DT; p=1e-22.

- **rs738408–PNPLA3** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs738409–PNPLA3** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs11748027–POLK** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.
  - External-only gene suggestion: [ANKDD1B](https://www.ebi.ac.uk/gwas/variants/rs11748027) — GWAS Catalog association row retrieved for the variant: trait=Low-density lipoprotein levels; mapped_genes=ANKDD1B; p=5e-148.

- **rs2519093–ABO** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs550057–ABO** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs360799–EHBP1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs3751674–ZFPM1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs6129786–ZHX3** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs4461246–EHBP1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs7220935–NPEPPS** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.
  - External-only gene suggestion: [KPNB1-DT](https://www.ebi.ac.uk/gwas/variants/rs7220935) — GWAS Catalog association row retrieved for the variant: trait=Vertical cup-disc ratio; mapped_genes=KPNB1-DT; p=2e-11.

- **rs8072100–NPEPPS** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs6129785–ZHX3** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs12935117–ZFPM1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs6129750–TOP1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs56373728–EHBP1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs10168771–EHBP1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.

- **rs2710644–EHBP1** (CONTEXT_ONLY):
  - Only variant-, locus-, or gene-level trait context was found; the exact mechanism is unresolved.
  - Curator note: Generated by query_external_evidence.py with conservative automatic matching; review exact mechanistic claims before upgrading evidence.


## Interpretation limits

- PubMed, GWAS Catalog, and Open Targets serve different evidence roles; database-hit counts are not summed as independent causal support.
- M5, M7, and KG claims derived from M2 or other local modules are lineage annotations, not extra independent votes.
- AlphaGenome Summary supplies variant-level regulatory context and cannot nominate a target gene by itself.
- Directional mechanism claims require explicit effect/risk-allele harmonization across GWAS and molecular assays.
- A failed, partial, ambiguous, or absent external query never implies novelty.
