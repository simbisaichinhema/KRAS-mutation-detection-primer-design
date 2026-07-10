# Allele-Specific Primer Design for KRAS Mutation Detection

**Author:** Simbisai Chinhema
**License:** [CC-BY-4.0](LICENSE)
**Status:** Academic / educational project

---

##  Overview

This project designs a mutation-specific primer for detecting oncogenic
variants of the **KRAS** gene using **allele-specific PCR (AS-PCR)** principles.

KRAS is a normal gene involved in cell signalling, but specific point mutations
(e.g., **G12D**) lead to uncontrolled cell proliferation and cancer. These
mutations involve a single nucleotide change, which makes precise detection
challenging. By placing the mutation at the 3′ end of a primer, an AS-PCR assay
can discriminate mutant from wild-type DNA in a simple two-reaction format.

## Objective

To design a forward primer that selectively amplifies the mutant KRAS sequence
by anchoring the mutation at the 3′ end of the primer, enabling discrimination
between mutant and wild-type DNA.

## Experimental Design

The assay uses a **two-reaction system**:

1. **Mutation-specific PCR**
   - Uses a primer designed to match the mutant sequence.
   - Amplifies only if the mutation is present.
2. **Control PCR**
   - Uses a general primer targeting KRAS.
   - Confirms DNA quality and PCR functionality.

##  Methodology

1. **Sequence retrieval** — Targeted extraction of KRAS Exon 2 from NCBI
   RefSeq (NM_004985). The wild-type reference is stored in
   [`data/kras_sequence.fasta`](data/kras_sequence.fasta) and the codon-12
   target region in [`data/kras_target_region.txt`](data/kras_target_region.txt).
2. **Primer design** — Primer3 for thermodynamic optimisation (Tm, GC%) with
   manual adjustment for 3′ terminal specificity.
3. **Validation** — In-silico validation via NCBI BLAST to confirm specificity
   and rule out off-target binding.

## 🔬 Primer Set

The designed primer set is documented in
[`results/primers.txt`](results/primers.txt). Summary:

| Primer | Sequence (5′→3′) | Len | GC% | Role |
| --- | --- | --- | --- | --- |
| KRAS_G12D_Forward | `ACTTGTGGTAGTTGGAGCTGA` | 21 bp | 47.6% | Mutant-specific (3′ A) |
| KRAS_WT_Forward | `ACTTGTGGTAGTTGGAGCTGG` | 21 bp | 52.4% | Wild-type control (3′ G) |
| KRAS_Common_Reverse | `TGTATCGTCAAGGCACTCTTGC` | 22 bp | 50.0% | Shared reverse |

> All Tm/GC% values are in-silico estimates and must be re-validated in
> Primer3 and BLAST before experimental use.

##  Repository Structure

```
kras-mutation-primer-design/
├── README.md                      # Project documentation
├── LICENSE                        # CC-BY-4.0 license
├── CITATION.cff                   # Citation metadata
├── data/
│   ├── kras_sequence.fasta        # KRAS Exon 2 wild-type reference (NM_004985)
│   └── kras_target_region.txt     # Codon-12 target region
├── results/
│   └── primers.txt                # Designed primer set
├── notebook/
│   └── design_notes.md            # Step-by-step design rationale
└── presentation/                  # Slides / figures (to be added)
```

##  Usage / Reproduction

This is a documentation and reference-data project — there is no executable
code to install or run. To reproduce or extend the work:

1. **Inspect the reference sequence**
   ```bash
   cat data/kras_sequence.fasta
   cat data/kras_target_region.txt
   ```
2. **Review the designed primers**
   ```bash
   cat results/primers.txt
   ```
3. **Re-validate in silico**
   - Load `data/kras_sequence.fasta` (and a G12D mutant variant) into
     [Primer3](https://primer3.ut.ee/) to confirm Tm, GC%, and amplicon size.
   - Run each primer against the human reference in
     [NCBI BLAST](https://blast.ncbi.nlm.nih.gov/) to confirm specificity.
4. **Follow the design rationale** in
   [`notebook/design_notes.md`](notebook/design_notes.md).

##  Expected Results

- **Specificity** — Successful amplification produces a distinct band on a gel
  (or a Ct value in qPCR) for mutant templates, with no amplification (or a
  significantly delayed Ct) for wild-type templates.
- **Sensitivity** — The optimised primer set should detect the G12D mutation at
  a concentration as low as 1% in a wild-type background.

##  Validation

- **In-silico specificity:** NCBI BLAST against the human genome.
- **Thermodynamic checks:** Tm, GC%, 3′ stability, and absence of
  self-/cross-dimerisation (Primer3 / OligoAnalyzer).
- **Wet-lab confirmation:** gel electrophoresis or qPCR on characterised
  mutant and wild-type controls.

## Future Improvements

- **Multiplexing** — Combine multiple allele-specific primers in a single
  reaction to detect several KRAS mutations (G12V, G12C, G13D) simultaneously.
- **LNA modification** — Incorporate Locked Nucleic Acids (LNAs) at the
  mutation site to increase the Tm difference between match and mismatch.
- **Digital PCR (dPCR)** — Transition the validated primers to a dPCR platform
  for absolute quantification of mutant load.

##  Citation

If you use this work, please cite it. A machine-readable citation is provided
in [`CITATION.cff`](CITATION.cff):

> Chinhema, S. (2026). *Allele-Specific Primer Design for KRAS G12D Mutation
> Detection*. CC-BY-4.0.

##  License

This work is licensed under the
[Creative Commons Attribution 4.0 International License (CC-BY-4.0)](LICENSE).
You are free to share and adapt it for any purpose, including commercially,
provided appropriate credit is given. See the [`LICENSE`](LICENSE) file for the
full terms.

## Contributing

Contributions, corrections, and additional validated primers are welcome.
Please open an issue or pull request describing the change. For substantial
changes, open an issue first to discuss the approach.

##  Disclaimer

This project was developed for **academic and educational purposes**. The
primers and protocols are provided as-is, without warranty, and are **not**
intended for clinical, diagnostic, or therapeutic use. Validate all reagents
and procedures in your own laboratory before any experimental application.

---

*Authored by Simbisai Chinhema.*
