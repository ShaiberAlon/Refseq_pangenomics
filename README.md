# Bfrag_pangenomics
Using assembly_summary_refseq.txt from

  `ftp://ftp.ncbi.nlm.nih.gov/genomes/refseq/assembly_summary_refseq.txt`

I coppied the second row (contains the titles for the table):

  `sed '2!d' assembly_summary_refseq.txt > BfragRefseqAssemblies.txt`
  
I _grepped_ all the Bacteroides fragilis, by running:

  `grep 'Bacteroides fragilis' assembly_summary_refseq.txt >> BfragRefseqAssemblies.txt`
  
There were 107 results. To create a list of ftp addresses for download I used:

  `cut -f 20 BfragRefseqAssemblies.txt > BfragRefseqAssembliesFTP.txt`
  
I then used:

  ``for file in `cat BfragRefseqAssembliesFTP.txt`;do wget --recursive --no-host-directories --cut-dirs=2 $file/``
  
After downloading all genomes I went throught the Pan-genome workflow.
