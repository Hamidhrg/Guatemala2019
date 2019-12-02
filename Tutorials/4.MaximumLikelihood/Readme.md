# Maximum-Likelihood Phylogenetic Inference

## **RAxMLGUI2.0**

In this tutorial we will learn how to perform a Maximum Likelihood (*ML*) analysis in *RAxML* (Randomized Axelerated Maximum Likelihood), which is a program for sequential and parallel Maximum Likelihood based inference of large phylogenetic trees. You can compile the code from [here](https://github.com/stamatak/standard-RAxML) which works with command line. However, for this practical we will use raxmlGUI 2.0 ([Edler et al. 2019](https://www.biorxiv.org/content/10.1101/800912v1)), a graphical user interface (*GUI*) for RAxML. raxmlGUI 2.0 facilitates phylogenetic analyses by coupling an intuitive interface with the unmatched performance of RAxML. You can download the graphical interface ramlGUI 2.0 for Windows, MacOSX and Linux [here](https://antonellilab.github.io/raxmlGUI/).

**Tree inference**

The graphical interface is very user-friendly. It is important that you create a folder and place the corresponding data files (one file per gene). By clicking on "LOAD ALIGNMENT" a dialog will open where you can select your alignments. raxmlGUI 2.0 only supports Phylip format, so you should save your files in this format.

So the first step for you will be to open *Aliview*, load your gene alignment files `4_Cats_ATP6.fasta, 4_Cats_COI.fasta, 4_Cats_CytB.fasta & 4_Cats_ND5.fasta` and save them in phylip format. Then you should have the following files:

```
4_Cats_ATP6.phy
4_Cats_COI.phy
4_Cats_CytB.phy
4_Cats_ND5.phy
```

One of the advantages of *raxmlGUI 2.0* is that you can select the number of processors to work with and, therefore, on computers with multiple processors, this greatly accelerates the calculation process. This is selected in the red rectangle at top right of the next picture (choose the maximum number you have there):
 
<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/4.MaximumLikelihood/RAxML1.jpg" alt="RAxML1" width="800"></p>

The other red rectangle is where you can click to upload your alignments. Click there and upload your phylip format alignments. RAxML is a program that only allows the implementation of 4 nucleotide evolutionary models: GTR; GTR+G (GTRGAMMA); GTR+G+I (GTRGAMMAI); GTR+I (GTRI). For this exercise choose GTR+G+I.

<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/4.MaximumLikelihood/RaxML2.png" alt="RaxML2" width="800"></p>

Once you upload the alignment, choose the type of *analysis* that in our case is going to be an ML+rapid bootstrap. Now you will be modifying the substitution model to *GTRGAMMAI* in the smaller red rectangle. Then select *reps* which indicates the number of bootstrap replicates we want to do. In this practical we will leave it at 100 but normally it is advisable to do 1000. 

*BS brL* Indicates whether you want to store the branch lengths on each of the bootstrap trees. This increases the computing time and therefore we leave it at default. Now define the output folder in the bigger red recangle and name your **Output name id** `RaxMLout`. The *outgroup* window allows you to select the outgroup. It is not necessary to define an outgroup a priori. Now click run! this will show you the program running on the console part.

Once a job is finished we have created several files. The file `RAxML_bipartitions.RaxMLout.tre` is the one that contains the best inferred tree with the boostrap values for the nodes. Open the *FigTree* program. Open the `RAxML_bipartitions.RaxMLout.tre` file in *FigTree*. As we have not used any outgroup in our dataset, we can use our prior knowledge about cats to reroot the tree! Genera *Panthera* and *Neofelis* form a monophyletic group which is the sister group to all other felids. Use this information to reroot the tree! Check the bootstrap values in the tree. How do you interpret them? Which parts of the tree are not well supported?




