# Design Notes: Allele-Specific Primer Design for KRAS G12D

## Why KRAS was Selected
The KRAS gene is one of the most frequently mutated oncogenes in human cancers, particularly in pancreatic, colorectal, and lung adenocarcinomas. Detecting specific mutations is crucial for clinical diagnostics, as KRAS status often determines the eligibility for targeted therapies (e.g., EGFR inhibitors).

## What Mutation (G12D) Means
- **Mutation:** G12D (Glycine to Aspartic Acid at Codon 12).
- **Genetic Change:** A transition at the second position of codon 12 (**GGT** to **GAT**).
- **Impact:** This mutation impairs the intrinsic GTPase activity of the KRAS protein, locking it in a constitutive "on" state, which drives uncontrolled cellular proliferation.

## Primer Design Workflow

### Step 1: Identify Mutation Site (Anchor Point)
In the provided KRAS Exon 2 sequence, the target is **Codon 12**.
- **Wild-Type:** GGT (Glycine)
- **Target Position:** The second nucleotide (G) of codon 12.
- **Mutation (G12D):** G → A transition.

### Step 2: Extract Local Region
Using the mutation site as the center, we utilize the following specific segment of the KRAS gene:
- **Target Region:** `ATATAAACTTGTGATAGTTGGAGCTGGTGGCGTAGGCAAGAGTGCCTTGACGATACAGCTA`

### Step 3: Create Mutant Sequence
- **WT:** `...GTAGTTGGAGCT GGT GGC...`
- **MUT:** `...GTAGTTGGAGCT GAT GGC...` (Target base is 'A')

### Step 4: Design the Primer
The primer must terminate precisely at the mutation site (3′ end) to ensure allele-specific extension.
- **Forward Primer (21 bp):** `5'- ACTTGTGGTAGTTGGAGCTGA -3'`
- **3′ End:** Terminal 'A' matches the G12D mutation.

### Step 5: Check Basic Parameters
- **Length:** 21 bp (Within 18–22 bp range)
- **GC%:** ~47.6% (Within 40–60% range)
- **3′ Stability:** Ends in `...GCTGA`, providing stable but not excessive binding at the critical end.

### Step 6: Predicted Behavior
- **Mutant Template:** Perfect match at 3′ end allows DNA polymerase to extend.
- **Wild-Type Template:** Mismatch at 3′ end (A:G) inhibits polymerase extension.
- **Result:** Selective amplification of the G12D allele.

