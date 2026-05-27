# Reference List Errors in Our Oikos Paper

After publication of our paper in Oikos (https://nsojournals.onlinelibrary.wiley.com/doi/10.1002/oik.12167), we discovered some errors in the reference list. Because these errors originated from an automated LaTeX compilation correction process, we are documenting here exactly how the issue occurred, which references were affected, and what lessons were learned.

## How the Problem Happened

During manuscript preparation in LaTeX, three references in the `.bib` file contained problematic characters that prevented successful compilation of the reference list and PDF generation. These characters likely originated either from manual entry or from exported citation metadata.

To diagnose and fix the compilation problem, an automated compilation-repair tool available on the LaTeX platform (Overleaf.com) was used. The tool successfully restored compilation and allowed the PDF to be generated. We then used these files that successfully compiled in or local LaTex workflow.

However, the automated repair process silently rewrote portions of several BibTeX entries instead of only correcting the malformed characters. Critically:

- the citation keys were preserved;
- parts of the metadata were preserved (typically year and at least one author name);
- but other fields were replaced or corrupted.

Because the citation keys remained unchanged, the issue was difficult to detect during manuscript proofreading. For example, citations in the manuscript still appeared as `LessovSchlaggar2016`, giving the impression that nothing had changed, while the underlying BibTeX entry had been rewritten incorrectly.

This was the first manuscript we prepared fully in LaTeX, and at the time we were unaware that automated compilation-repair tools could introduce this type of silent metadata corruption.

## Affected References and Corrections

### 1. Incorrect Reference

> Schlaggar, B. L. and Laumann, T. O. 2016. Functional brain networks in childhood, adolescence, and adulthood. – NeuroImage 129: 313–323.

### Correct Reference

> Lessov-Schlaggar, C. N., Rubin, J. B. and Schlaggar, B. L. 2016. The fallacy of univariate solutions to complex systems problems. – Frontiers in Neuroscience 10: 267.

---

### 2. Incorrect Reference

> Bonn, N. A. and Bouter, L. M. 2021. Policy versus practice: a systematic review of the role of research assessment systems in promoting research integrity. – Research Integrity and Peer Review 6: 14.

### Correct Reference

> Aubert Bonn, N. and Pinxten, W. 2021. Rethinking success, integrity, and culture in research (part 2) – a multi-actor qualitative study on problems of science. – Research Integrity and Peer Review 6(1): 3. https://doi.org/10.1186/s41073-020-00105-z

---

### 3. Incorrect Reference

> Muff, S., Amrhein, V. and Furrer, R. 2022. Rewriting results sections in the language of evidence. – Trends Ecol. Evol. 37: 203–210.

### Correct Reference

> Muff, S., Nilsen, E. B., O’Hara, R. B. and Nater, C. R. 2022. Rewriting results sections in the language of evidence. – Trends in Ecology & Evolution 37(3): 203–210.

---

### 4. Incorrect Reference

> Wootton, J. T., Power, M. E. and Paine, R. T. 2017. Effects of productivity, consumers, and decoupling on food web processes and ecosystem structure. – Annu. Rev. Ecol. Evol. Syst. 48: 1–26.

### Correct Reference

> Wootton, K. L. 2017. Omnivory and stability in freshwater habitats: Does theory match reality? – Freshwater Biology 62: 821–832. https://doi.org/10.1111/fwb.12908

## Why the Errors Were Difficult to Detect

Several aspects made these problems particularly difficult to identify:

1. **Citation keys remained unchanged**  
   Since LaTeX citations in the manuscript continued to point to the same keys, the manuscript text itself appeared normal.

2. **Partial metadata preservation**  
   The automated rewrite often preserved:
   - publication year;
   - at least one author name;
   - sometimes the journal name.

   This made the corrupted entries plausible.

3. **Compilation succeeded afterward**  
   Once the automatic repair tool fixed the compilation issue, the manuscript compiled normally and no further warnings were generated.



## Lessons Learned

This experience highlighted an important risk associated with automated LaTeX/BibTeX repair tools:

- successful compilation does **not** guarantee citation integrity;
- automatic repair systems may silently rewrite bibliographic metadata;
- preserving citation keys can conceal corrupted references.

As a consequence, we now strongly recommend:

1. manually reviewing all modified BibTeX entries after automatic repairs;
2. comparing generated references against original sources;
3. avoiding blind acceptance of automated compilation fixes.

We are documenting this publicly both for transparency and to help other researchers avoid similar problems in future LaTeX workflows.
