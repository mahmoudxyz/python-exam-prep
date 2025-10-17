# DNA/RNA Translator

## The Challenge

Build a command-line tool that translates DNA sequences to proteins. Handle DNA → RNA transcription and RNA → Protein translation. Design however you want.

## What to Support

### Required Features:

- DNA to RNA transcription
- RNA to Protein translation (using standard genetic code)
- Find Open Reading Frames (ORFs)
- Reverse complement of DNA
- Handle start codon (ATG/AUG) and stop codons
- Read sequences from command line or file

### Bonus Features:

- All 6 reading frames (3 forward + 3 reverse)
- Multiple genetic codes (standard, mitochondrial, etc.)
- Find longest ORF
- GC content calculation
- Statistics output

---

## Input/Output Examples

### Example 1: DNA to RNA

**Input:**

```
DNA: ATCGATCG
```

**Output:**

```
RNA: AUCGAUCG
```

---

### Example 2: RNA to Protein

**Input:**

```
RNA: AUGGCCAUUGUAUGA
```

**Output:**

```
Protein: MAI*
(Met-Ala-Ile-STOP)

Details:
AUG → Met (Start codon)
GCC → Ala
AUU → Ile
GUA → Val (incomplete codon, not translated)
UGA → STOP
```

---

### Example 3: DNA to Protein (Complete)

**Input:**

```
DNA: ATGGCCATTGTAUGA
```

**Output:**

```
Step 1 - Transcription:
DNA: ATGGCCATTGTAUGA
RNA: AUGGCCAUUGUAUGA

Step 2 - Translation:
Protein: MAI*

Amino Acids:
1. AUG → Met (M) [Start]
2. GCC → Ala (A)
3. AUU → Ile (I)
4. GUA → (incomplete)
5. UGA → STOP (*)
```

---

### Example 4: Reverse Complement

**Input:**

```
DNA: ATCG
```

**Output:**

```
Original:           5'-ATCG-3'
Complement:         3'-TAGC-5'
Reverse:            3'-GCTA-5'
Reverse Complement: 5'-CGAT-3'
```

---

### Example 5: Find ORFs

**Input:**

```
DNA: CCCATGGCCATTGATAACCCATGGGCTAA
```

**Output:**

```
Found 2 ORFs:

ORF 1:
Position: 3-17
DNA: ATGGCCATTGATAA
RNA: AUGGCCAUUGAUAA
Protein: MAI* (incomplete - no stop codon)
Length: 14 bp (4 codons)

ORF 2:
Position: 20-29
DNA: ATGGGCTAA
RNA: AUGGGCUAA
Protein: MG*
Length: 9 bp (3 codons)
```

---

### Example 6: All Reading Frames

**Input:**

```
DNA: ATGGCCATAG
```

**Output:**

```
=== FORWARD STRAND ===

Frame +1: ATGGCCATAG
RNA:      AUGGCCAUAG
Protein:  MA*

Frame +2: TGGCCATAG
RNA:      UGGCCAUAG
Protein:  WP* (no start codon)

Frame +3: GGCCATAG
RNA:      GGCCAUAG
Protein:  GP (no start/stop)

=== REVERSE STRAND ===
Reverse Complement: CTATGGCCAT

Frame -1: CTATGGCCAT
RNA:      CUAUGGCCAU
Protein:  LWP (no start codon)

Frame -2: TATGGCCAT
RNA:      UAUGGCCAU
Protein:  YGH (no start codon)

Frame -3: ATGGCCAT
RNA:      AUGGCCAU
Protein:  MA (no stop codon)
```

---

## Genetic Code Table

Use the standard genetic code:

```
# Start Codon
ATG (AUG) → Methionine (Met, M) [START]

# Stop Codons
TAA (UAA) → STOP (*)
TAG (UAG) → STOP (*)
TGA (UGA) → STOP (*)

# All Codons (RNA)
UUU, UUC → Phe (F)
UUA, UUG, CUU, CUC, CUA, CUG → Leu (L)
UCU, UCC, UCA, UCG, AGU, AGC → Ser (S)
UAU, UAC → Tyr (Y)
UGU, UGC → Cys (C)
UGG → Trp (W)
CCU, CCC, CCA, CCG → Pro (P)
CAU, CAC → His (H)
CAA, CAG → Gln (Q)
CGU, CGC, CGA, CGG, AGA, AGG → Arg (R)
AUU, AUC, AUA → Ile (I)
AUG → Met (M)
ACU, ACC, ACA, ACG → Thr (T)
AAU, AAC → Asn (N)
AAA, AAG → Lys (K)
GUU, GUC, GUA, GUG → Val (V)
GCU, GCC, GCA, GCG → Ala (A)
GAU, GAC → Asp (D)
GAA, GAG → Glu (E)
GGU, GGC, GGA, GGG → Gly (G)
```

You can represent this as a dictionary in your code:

```python
CODON_TABLE = {
    'AUG': 'M', 'UUU': 'F', 'UUC': 'F',
    'UUA': 'L', 'UUG': 'L', 'UCU': 'S',
    # ... etc
    'UAA': '*', 'UAG': '*', 'UGA': '*'
}
```

---

## Command Line Interface

### Interactive Mode:

```bash
$ python dna_translator.py

=== DNA/RNA TRANSLATOR ===

1. DNA → RNA
2. RNA → Protein
3. DNA → Protein
4. Find ORFs
5. Reverse Complement
6. All Reading Frames
0. Exit

Enter choice: 3

Enter DNA sequence: ATGGCCATTGTAUGA

[Output shown above]
```

### File Mode:

```bash
$ python dna_translator.py sequences.txt

# Reads DNA sequences from file (one per line)
# Translates each and shows results
```

### Direct Mode:

```bash
$ python dna_translator.py ATGGCCATAG

# Translates the sequence directly
```

---

## Example File Format

**Input file: `sequences.txt`**

```
ATGGCCATTGTAUGA
ATGGGCTAA
CCCATGGCCATTGATAACCCATGGGCTAA
```

**Output:**

```
Sequence 1: ATGGCCATTGTAUGA
Protein: MAI*
Length: 15 bp

Sequence 2: ATGGGCTAA
Protein: MG*
Length: 9 bp

Sequence 3: CCCATGGCCATTGATAACCCATGGGCTAA
Found 2 ORFs (see details above)
```

---

## What You'll Practice

- String manipulation (slicing, iteration)
- Dictionaries (codon table lookup)
- Functions (transcription, translation, ORF finding)
- Lists (storing codons, proteins, ORFs)
- File I/O (reading sequences)
- Loops and conditionals
- Algorithm design (finding patterns)
- Data structures (organizing results)

## Edge Cases to Handle

- Incomplete codons (sequence length not divisible by 3)
- No start codon found
- No stop codon found
- Empty sequences
- Invalid characters (not A, T, C, G, U)
- Case insensitivity (accept both upper and lowercase)

---

## Success Criteria

✅ DNA → RNA transcription works correctly  
✅ RNA → Protein translation with codon table  
✅ Finds ORFs (start to stop codon)  
✅ Reverse complement calculated correctly  
✅ Handles edge cases gracefully  
✅ Clear output formatting  
✅ Works from command line

## Time Estimate

2-3 hours for basic features, 4-5 hours with all reading frames and ORF finding

---

## Tips

### Start Simple:

1. Implement DNA → RNA first (just replace T with U)
2. Add codon table dictionary
3. Implement basic translation (no ORF logic)
4. Add start/stop codon detection
5. Implement ORF finding
6. Add reading frames last

### Useful String Operations:

```python
# Split sequence into codons
sequence = "ATGGCCATAG"
codons = [sequence[i:i+3] for i in range(0, len(sequence), 3)]
# Result: ['ATG', 'GCC', 'ATA', 'G']

# Reverse complement
complement = {'A': 'T', 'T': 'A', 'C': 'G', 'G': 'C'}
rev_comp = ''.join(complement[base] for base in reversed(sequence))
```

### Reading Frames:

```python
# Frame +1: start at position 0
# Frame +2: start at position 1
# Frame +3: start at position 2
for frame in range(3):
    subseq = sequence[frame:]
    # translate subseq
```

---

## Validation

Test your program with these sequences:

**Test 1:** `ATGGCCATAG`

- Should produce: `MA*`

**Test 2:** `ATGGGCTAA`

- Should produce: `MG*`

**Test 3:** `TTTATGTAG`

- Should produce: No ORF in frame +1 (no ATG at start)

**Test 4:** `ATGGGGGGG`

- Should produce: `MGG` (incomplete, no stop codon)

---

## Submit Your Solution

Save as `solutions/yourname_dna_translator.py`

Test with the examples above to verify correctness!
