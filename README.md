# Deephos
Improving the sensitivity and specificity of TMT-labeled phosphopeptide identification using deep learning

1. Usage:
Command  : java -jar deephos.jar <options> <file>
Options  :
  -i <parameter_file> : Config file path for search parameters [Required]
  
Example : java -Xmx20G -jar deephos.jar -i foo.params

2. In silico spectral library predicted by Deephos can be downloaded from https://drive.google.com/file/d/1z7wacIIrRCgwQt3HxSOanAPDVY-I-Lj_/view?usp=sharing.
 1) Unzip the downloaded file. There are two files, TmtPhospho_deephos_library.mgf and decoy_deephos_library.mgf.
 2) TmtPhospho_deephos_library.mgf: For ~8,000 human phosphoproteins annotated in UniProt, trypsin-digested peptides with up to 1 missed cleavage were in silico generated and STY-containing peptides were modified allowing up to two phosphorylation sites. Deephos predicted the fragment ions of all the theoretical phosphopeptides assuming precursor charge states of 2+, 3+ and 4+, resulting 13,156,857 predicted MS/MS spectra.
 3) decoy_deephos_library.mgf for target-decoy search: Deephos predicts fragment ions of reverse peptides generated from target peptides to construct decoy spectra. 
  
