# TooT-T
This tool predicts transporter proteins.
 
Input: proteins sequences in Fasta format
Output: the predicted class,1=transporter, 0=non-transporter


The method used in this tool is described in:
<a id="1">[1]</a> 
Alballa, Munira, and Gregory Butler. "TooT-T: discrimination of transport proteins from non-transport proteins." BMC bioinformatics 21 (2020): 1-10

However, it was trained with updated dataset retrieved from the Swiss-Port database as follows:

This GO MF was chosen here because it is directly related to the actual function of the protein rather than the general process in which it is involved.




## FOLDERS
There are a number of folders that support the running of TooT-T and its outputs.

### dataset/transporter_substrate_class
Contains both the training and the independent testing dataset if fasta format, the identifiers of independent testset is found under substrate_classes_indep.csv.
The models were trained using the training dataset =(all dataset - independent testset)



### intermediate_files
Contains the homology details needed to extract the features. Details of the  `psi Blast hits` for each sequence is found here.

intermediate_files/Compositions: Contains the extracted `psi_composition` features of test set

### db
Contains the database to be used when performing psiBLAST as well as TCDB for ATH predictions.


### src
The scripts needed to use the tool.

## HOW TO USE
 - This tool requires that `BLAST` be pre-installed
 -This tool requires that M-View to  be pre-installed (link https://desmid.github.io/mview/)
 - Usage: `Rscript src/TooT_T.R -query=<input> [-TooTT=<TooTTdir>] [-out=<outdir>] [-db=<path to dbs>]`
  - `<input>` is your sequence input file in fasta format
  - `<out>` is the output directory where you want the predicted 	results, formatted as csv
  - `<TooTTdir>` is the directory where the base TooT-T files 	are located
  - `<db> is the directory where the databases (for psi-compositions) is stored in addition to TCDB for ATH predictions`
 - `psi-compositions` features of each sequence in the test set is  found under [intermediate_files/Compositions/](intermediate_files/Compositions/)
