# Deephos
Improving the sensitivity and specificity of TMT-labeled phosphopeptide identification using deep learning

##################################################################

1. Usage
- Command: java -jar deephos.jar -i <parameter_file: config file path for search parameters, required>
- Example: java -Xmx20G -jar deephos.jar -i foo.params

##################################################################

2. In silico spectral library predicted by Deephos
- TMT(229.162932) library can be downloaded from https://drive.google.com/file/d/1EtKatZOiDNMCNtr1M2d66hOAKZUzrPg0/view?usp=share_link
- TMTpro(304.207146) from https://drive.google.com/file/d/1L_FyZz7fjzYx7Ka9akc2dbZvRnmyYzNg/view?usp=share_link
- Unzip the downloaded file. There are two files, target_tmt###.dpslib and decoy_tmt###.dpslib
- target_tmt###.dpslib: For ~8,000 human phosphoproteins annotated in UniProt, trypsin-digested peptides with up to 1 missed cleavage were in silico generated and STY-containing peptides were modified allowing up to two phosphorylation sites. Deephos predicted the fragment ions of all the theoretical phosphopeptides assuming precursor charge states of 2+, 3+ and 4+, resulting 13,156,857 predicted MS/MS spectra.
- decoy_tmt###.dpslib for target-decoy search: Deephos predicts fragment ions of reverse peptides generated from target peptides to construct decoy spectra.

##################################################################

3. FDR Analysis
- Command: java -Xmx3G -cp deephos.jar deephos.TDA <-options>
- Options: 1) -i <path to search result file or directory, required>, Given a directory, the results files in it are analyzed all together.
           2) -fdr <0.00 ~ 1.00, required>, 
           3) -o <path to fdr-filtered id file, optional>
- Example1: java -Xmx3G -cp deephos.jar deephos.TDA -i results.tsv -fdr 0.01 (*fdr0.01_id.tsv file is generated)
- Example2: java -Xmx3G -cp deephos.jar deephos.TDA -i results.tsv -o finalResult.tsv -fdr 0.01
