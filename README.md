# Deephos
Improving the sensitivity and specificity of TMT-labeled phosphopeptide identification using deep learning

##################################################################

1. Usage
- Command: java -jar deephos.jar -i <parameter_file: config file path for search parameters, required>
- Example: java -Xmx20G -jar deephos.jar -i foo.params

##################################################################

2. In silico spectral library predicted by Deephos can be downloaded from https://drive.google.com/file/d/1z7wacIIrRCgwQt3HxSOanAPDVY-I-Lj_/view?usp=sharing.
- Unzip the downloaded file. There are two files, TmtPhospho_deephos_library.mgf and decoy_deephos_library.mgf.
- TmtPhospho_deephos_library.mgf: For ~8,000 human phosphoproteins annotated in UniProt, trypsin-digested peptides with up to 1 missed cleavage were in silico generated and STY-containing peptides were modified allowing up to two phosphorylation sites. Deephos predicted the fragment ions of all the theoretical phosphopeptides assuming precursor charge states of 2+, 3+ and 4+, resulting 13,156,857 predicted MS/MS spectra.
- decoy_deephos_library.mgf for target-decoy search: Deephos predicts fragment ions of reverse peptides generated from target peptides to construct decoy spectra.

##################################################################

3. FDR Analysis
- Command: java -Xmx3G -cp deephos.jar deephos.TDA <-options>
- Options: 1) -i <path to search result file, required>, 2) -fdr <0.00 ~ 1.00, required>, 3) -o <path to fdr-filtered id file, optional>
- Example1: java -Xmx3G -cp deephos.jar deephos.TDA -i results.tsv -fdr 0.01 (*fdr0.01_id.tsv file is generated)
- Example2: java -Xmx3G -cp deephos.jar deephos.TDA -i results.tsv -o finalResult.tsv -fdr 0.01
