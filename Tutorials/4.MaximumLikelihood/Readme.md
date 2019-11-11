# Maximum-Likelihood Phylogenetic Inference


## **Part I: IQTREE** 

In this tutorial, we will analyse the butterfly dataset with one of the fastest maximum-likelihood based phylogenetic programs [IQ-TREE](http://www.iqtree.org) ([Nguyen et al. 2015](https://academic.oup.com/mbe/article/32/1/268/2925592)). IQ-TREE for Windows, MacOSX and Linux can be downloaded [here](http://www.iqtree.org/#download), you can install it on your personal computer (optional).

The quickest is to try out the IQ-TREE web server, where you only need to upload an alignment, choose the options and start the analysis.

**Tree inference**

Tree Inference provides the most frequently used features of IQ-TREE and allows users to carry out phylogenetic analysis on a multiple sequence alignment (MSA). In the most basic case, no more than an MSA file is required to submit the job. Without further input, IQ-TREE will run with the default parameters and auto-detect the sequence type as well as the best-fitting substitution model. Additionally, Ultrafast Bootstrap ([Hoang et al., 2018](https://academic.oup.com/mbe/article/35/2/518/4565479)) and the SH-aLRT branch test ([Guindon et al., 2010](https://academic.oup.com/sysbio/article/59/3/307/1702850)) will be performed.
You can either try out the web server with an example alignment by ticking the corresponding box or upload your own alignment file. By clicking on ‘Browse’ a dialog will open where you can select your MSA; the file formats Phylip, Fasta, Nexus, Clustal and MSF are supported.

<p align="center"><img src="http://www.iqtree.org/doc/images/tut1.png" alt="IQTREE" width="600"></p>

After that you can submit the job. If you provide an email address, a notification will be sent to you once the job is finished. In case you don’t specify an email address, you will receive a link in the next step; you can bookmark this link to retrieve your results after the job is finished.

**Model Selection**

IQ-TREE supports a wide range of substitution models for DNA, protein, codon, binary and morphological alignments. In case you do not know which model is appropriate for your data, IQ-TREE can automatically determine the best-fit model for your alignment. Use the Model Selection tab if you only want to find the best-fit model without doing tree reconstruction.

<p align="center"><img src="http://www.iqtree.org/doc/images/tut2.png" alt="IQTREE" width="600"></p>

Like with Tree Inference, the only obligatory input is a multiple sequence alignment. You can either upload your own alignment file or use the example alignment to try out the web server and then submit the job.

**Analysis Results**

In the tab Analysis Results you can monitor your jobs. With our example file, a run will only take a few seconds, depending on the server load. For your own alignments the CPU time limit is 24 hours. If you provided an email address when submitting the job, you will get an email once it is finished.

<p align="center"><img src="http://www.iqtree.org/doc/images/tut3.png" alt="IQTREE" width="600"></p>

Once a job is finished, you can select it by checking the corresponding box and then downloading the selected jobs as a zip file. This zip file will contain the results of your run, including the Run Log and the Full Result which are also accessible in the webserver.

   Suffix	     Output File Explanation
- .iqtree	     Full result of the run, this is the main report file
- .log	       Run log
- .treefile	   Maximum likelihood tree in NEWICK format, can be visualized with treeviewer programs
- .svg	       Graphical tree representation in SVG format, done with ete view
- .pdf	       Graphical tree representation in PDF format, done with ete view
- .contree	   Consensus tree with assigned branch supports where branch lengths are optimized on the original alignment; printed if Ultrafast Bootstrap is selected
- .ckp.gz	    Checkpoint file; included if a job was stopped because of RAM/CPU limits.

This tutorial was retrieved from the [IQTREE Web-Server](http://www.iqtree.org/doc/Web-Server-Tutorial)

**Part II**

In the second part of this tutorial we will learn how to perform an ML analysis in RAxML (Randomized Axelerated Maximum Likelihood), which is a program for sequential and parallel Maximum Likelihood based inference of large phylogenetic trees. You can compile the code from [here](https://github.com/stamatak/standard-RAxML) which works with command line. However, for this practical we will use raxmlGUI 2.0 ([Edler et al. 2019](https://www.biorxiv.org/content/10.1101/800912v1)), a graphical user interface for RAxML. raxmlGUI 2.0 facilitates phylogenetic analyses by coupling an intuitive interface with the unmatched performance of RAxML. You can try to download the graphical interface ramlGUI 2.0 for Windows, MacOSX and Linux [here](https://antonellilab.github.io/raxmlGUI/).

**Tree inference**

The graphical interface is really friendly. It is very important that you create a folder and place the corresponding data files (one file per gene). By clicking on "LOAD ALIGNMENT" a dialog will open where you can select your MSA. raxmlGUI 2.0 only supports Phylip format, so you should save your files in this format. 

raxmlGUI 2.0 allows you to do many types of analyses and one of the advantages is that you can select the number of processors to work with and, therefore, on computers with multiple processors, this greatly accelerates the calculation process. 
 
<p align="center"><img src="https://github.com/niklas-w/Molecular-systematics-course/blob/master/Tutorials/4.MaximumLikelihood/RAxML1.png" alt="RAxML1" width="600"></p>

RAxML is a program that only allows the implementation of 4 nucleotide evolutionary models: GTR; GTR+G; GTR+I; GTR+G+I.

<p align="center"><img src="https://github.com/niklas-w/Molecular-systematics-course/blob/master/Tutorials/4.MaximumLikelihood/RAxML2.png" alt="RAxML2" width="600"></p>

Once you upload the alignment, choose the type of *analysis* that in our case is going to be an ML+rapid bootstrap. 

Then select *reps* which indicates the number of bootstrap replicates we want to do. In this practical we will leave it at 100 but normally it is advisable to do 1000. 

*BS brL* Indicates whether you want to store the branch lengths on each of the bootstrap trees. This increases the computing time and therefore we leave it at default.

The *outgroup* window allows you to select the outgroup. It is not necessary to define an outgroup a priori. 

Finally, there is a window with the evolutionary models. For DNA you can only choose one of the 4 models: GTR; GTR + G (GTRGAMMA); GTR + G + I (GTRGAMMAI); GTR + I (GTRI). According to the author of RAxML if the Gamma is implemented, it is no longer necessary to implement I (invariant sites). 

To incorporate partitions by gene we only need to upload the diffente gene files and the program automatically creates a concatenated alignment.
Finally, we can proceed with *Run* RAxML to start the tree search.

<p align="center"><img src="https://github.com/niklas-w/Molecular-systematics-course/blob/master/Tutorials/4.MaximumLikelihood/RAxML3.png" alt="RAxML3" width="600"></p>

Once a job is finished we have created several files. The file *.tre* is the one that contains the best inferred tree with the boostrap values for the nodes. Open the file *.tre* with the FigTree program. Check the bootstrap values in the tree and compare the corresponding ones with the result retrieved from the IQTREE analysis.

# Tree visualizations

Open the file .treefile retrieved from IQTREE and .tre from raxmlGUI 2.0 in FigTree and check the support values. The phylogeny should look more or less as shown in the next screenshot.

<p align="center"><img src="https://github.com/niklas-w/Molecular-systematics-course/blob/master/Tutorials/4.MaximumLikelihood/RAxML4.png" alt="RAxML4" width="600"></p>

**Questions**

1. Are the RAxML bootstrap values higher/lower compared to those recovered from the UFBoot2 in IQTREE?

2. Are the same nodes/relationships supported?




