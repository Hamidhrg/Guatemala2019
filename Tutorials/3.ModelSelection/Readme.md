# **Model Selection**


In the first two tutorials you have learned to download various gene sequences from Genbank and align and concatenate them to create a dataset to practice. You also heard about differences between different file formats and saw how to create the needed formats. For the next tutorial, we are going to use *PartitionFinder* to find the best partitioning scheme for a new dataset and also the best models for each partition. The new dataset is called `3_ConCATenated.fasta`. As you might guess from its name, it is a dataset of members of felidae family (cats, miauuuuu!). Go to [***Guatemala2019/Data/***](https://github.com/Hamidhrg/Guatemala2019/tree/master/Data) and download `3_ConCATenated.fasta`). Here we are using this dataset to see who scored higher when I asked about the relationships of the cats to find our **Catman** or **Catwoman** ;)

First remember that our dataset, `3_ConCATenated.fasta` is saved as a fasta format. Now open *Aliview* and open this file. You should have something similar to this:

<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/Aliview3.png" alt="Aliview3" width="800"></p>

Now I want you to save a \*.phy and a \.nex alignment file with the name **Dataset**. Use the options "***Save as Nexus***" and "***Save as Phylip (full names & padded)***" as seen in the next picture (both options marked with a red rectangle):

<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/Aliview5.png" alt="Aliview5" width="800"></p>

You should have these two files now:

```
3_ConCATenated.phy
3_ConCATenated.nex
```

For this tutorial we are going to use the `3_ConCATenated.phy` and a command file that we are going to create together. The command file has different blocks that you need to modify based on your analysis. In your text editor create a new file and save it as `partition_finder.cfg`. Copy/Paste inside the file the next block:

```
## ALIGNMENT FILE ##
alignment = infile.phy;

## BRANCHLENGTHS: linked | unlinked ##
branchlengths = linked;

## MODELS OF EVOLUTION: all | allx | mrbayes | beast | gamma | gammai | <list> ##
models = mrbayes;

# MODEL SELECCTION: AIC | AICc | BIC #
model_selection = BIC;

## DATA BLOCKS: see manual for how to define ##
[data_blocks]

**REPLACE THIS LINE BY YOUR PARTITIONS INFORMATION!**

## SCHEMES, search: all | user | greedy | rcluster | rclusterf | kmeans ##
[schemes]
search = greedy;

```

For ***ALIGNMENT FILE*** section you have to provide the name of the alignment file which is in this case `ConCATenated.phy`. But in this case as we are going to run the job on an online platform and the platform asks us to use `alignment = infile.phy;`. In the ***DATA BLOCKS*** you have to use the partition information that you have to download from the [***Guatemala2019/Data/***](https://github.com/Hamidhrg/Guatemala2019/tree/master/Data) page. The file is called `3_partitions.txt`. This is similar to what we prepared in the last tutorial, but here I just made it to speed up the tutorial. Take a look at the other options, what else can you modify? Remember to save the changes to your file.

Now create another command file called `partitionCodon_finder.cfg`. You will need to get the partition information from the [***Guatemala2019/Data/***](https://github.com/Hamidhrg/Guatemala2019/tree/master/Data) page again. And as I am very creative today I have called the file with the partition information `3_partitionsCodons.txt`! 

***But remeber that for running PartitionFinder on your computer*** you have to change in the `## ALIGNMENT FILE ##` section, in the `alignment = infile.phy;` the name of the alignment to your own alignment file, and save the configuration file always as `partition_finder.cfg`. 

***IMPORTANT NOTE*** as today the cipres website is down, go down to the Persian cat picture, and follow the tutorial from there!

<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/ArrowDown.png" alt="Arrow" width="500"></p>

## Cipres

We are going to use an online platform to run *PartitionFinder* to speed up the analysis and also to introduce you to running analyses remotely. The platform that we are going to use now is called ***CIPRES***. It is a very useful online platform using very fast super computers where you can run plenty of other programs also. But you need to register first, so click and open (in a new window) the following link: [www.phylo.org/portal2/login!input.action](https://www.phylo.org/portal2/login!input.action). You will see something like the next image. If you don’t have an account already, click on the option in the red rectangle and register.

<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/Cipres.png" alt="Cipres" width="800"></p>

When you log in you will see something like this:

<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/Cipres2.png" alt="Cipres2" width="800"></p>

You have to click on ***Create New Folder*** and as ***Label*** you use `Course`. Now under your "Folders" you have a folder named ***Course*** and 2 other folders inside of it. Like the following picture:

<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/Cipres3.png" alt="Cipres3" width="800"></p>

Click on ***Data*** subfolder then on ***Upload/Enter Data***. Now you should be able to add the needed files by clicking on ***Browse*** and selecting the `ConCATenated.phy` and `partitionCodon_finder.cfg` files. Now click on ***Task*** folder and ***Create New Task*** button. You should have something like the following:


<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/Cipres4.png" alt="Cipres4" width="600"></p>

Click on the ***Select Input Data*** button and choose your `ConCATenated.phy` file and click ***Select Data***. Now under ***Select Tools*** find the ***PartitionFinder2 on XSEDE*** option and click on it. Now click on ***10 Parameters Set*** to see the ones we have to modify. 
For ***Maximum Hours to Run*** choose `1` and in ***Select cfg file (you can also create one below)*** choose your `partitionCodon_finder.cfg` file. You should see something like the following image:

<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/Cipres5.png" alt="Cipres5" width="600"></p>

Now click on ***Save Parameters*** and click ok. Now you should see this:


<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/Cipres6.png" alt="Cipres6" width="800"></p>

Now in the ***Description*** write `PF1` and click on ***Save and Run Task***. Click ok. You will see this:

<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/Cipres7.jpg" alt="Cipres7" width="800"></p>

Here you can see that your task is "Running"! Refresh the page from time to time to see when the job is done! You can see this best in the red rectangle on top-left of the picture above under **Running Tasks = 1**. When the number is zero (i.e. you have no more running jobs!) you have to click on the button in the second red rectangle in the above picture, under **Action**, **View Status** or **View Output**.

Now we want to export the results to our computer! So now you should be seeing something like this:


<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/Cipres8.png" alt="Cipres8" width="800"></p>

Now we want to download the \*.zip file marked with the red rectangle again. Download it and extract the files so we can take a look at them. 

<p align="center"><img src="https://github.com/Hamidhrg/Guatemala2019/blob/master/Tutorials/3.ModelSelection/PersianCat.png" alt="PersianCat" width="800"></p>

**Today as the Cipres website is down, download `3_analysis.zip` from the [Guatemala2019/Data/](https://github.com/Hamidhrg/Guatemala2019/tree/master/Data) page and continue the exercise from here.**

Inside your `analysis.zip`, you will find a file called `best_scheme.txt`, open it in your preferred text editor. Now I will explain the different blocks of information you have in the result file. First, you should see something like the next block:

```
Settings used

alignment         : .\3_ConCATenated.phy
branchlengths     : linked
models            : JC, K80, SYM, F81, HKY, GTR, JC+G, K80+G, SYM+G, F81+G, HKY+G, GTR+G, JC+I, K80+I, SYM+I, F81+I, HKY+I, GTR+I, JC+I+G, K80+I+G, SYM+I+G, F81+I+G, HKY+I+G, GTR+I+G
model_selection   : bic
search            : greedy

```

In this block it tells you which alignments have been used, what we have chosen for the branchlenghts, which models have been considered, what criterion is used to choose the best model and finally what kind of search we have done in the model space. Now let’s take a look at the real result of the analysis. But first do you remember how many partitions we had in the beginning? Three codon positions for each gene, therefore 12 partitions to start with! Which partitions are similar? Which ones you think are similar enough that we could merge them in the same partition? Take a look at the following block to see if your guess was accurate enough!


```
Best partitioning scheme

Scheme Name       : step_5
Scheme lnL        : -43335.28643798828
Scheme BIC        : 88090.1375826
Number of params  : 166
Number of sites   : 5175
Number of subsets : 7

Subset | Best Model | # sites    | subset id                        | Partition names
1      | HKY+G      | 226        | f2c1be7e04d4e9da29f5a44a1eb788d0 | ATP6_pos1
2      | HKY+I+G    | 1211       | 82c73c361abe0cac0a253acfaa82a3a9 | ND5_pos1, ATP6_pos1, Cytb_pos1
3      | GTR+I+G    | 740        | 28ba51e5e5506d52f222b5d99548e660 | ATP6_pos1, COI_pos1
4      | SYM+I+G    | 514        | 7275a23ee7a5907b034b0985213aa715 | COI_pos1
5      | HKY+I      | 514        | 40419ec8c2e7a5340490ed010bb4502a | COI_pos1
6      | GTR+I+G    | 985        | b99819bf2ce9c29eee1d9e58cb94c67e | ND5_pos1, Cytb_pos1
7      | GTR+I+G    | 985        | b8d8979469541b8f690718e7380fae3c | ND5_pos1, Cytb_pos1
```

Here in the result you have 2 sub-blocks. In the first one you get some general information about your results as the likelihood of the scheme chosen as the best, or number of parameters or .... Then you can see the subsets chosen as the best scheme for partitioning. *Were you correct in your guess?* 

Next you see different blocks which can be used for running different programs. Here we are going to use the block for MrBayes first. You should be able to find it easily in your text editor. It should be similar to this:

```
begin mrbayes;

	charset Subset1 = 1-678\3;
	charset Subset2 = 3359-5175\3 2-678\3 2222-3357\3;
	charset Subset3 = 3-678\3 681-2220\3;
	charset Subset4 = 679-2220\3;
	charset Subset5 = 680-2220\3;
	charset Subset6 = 3358-5175\3 2221-3357\3;
	charset Subset7 = 3360-5175\3 2223-3357\3;

	partition PartitionFinder = 7:Subset1, Subset2, Subset3, Subset4, Subset5, Subset6, Subset7;
	set partition=PartitionFinder;

	lset applyto=(1) nst=2 rates=gamma;
	lset applyto=(2) nst=2 rates=invgamma;
	lset applyto=(3) nst=6 rates=invgamma;
	lset applyto=(4) nst=6 rates=invgamma;
prset applyto=(4) statefreqpr=fixed(equal);
	lset applyto=(5) nst=2 rates=propinv;
	lset applyto=(6) nst=6 rates=invgamma;
	lset applyto=(7) nst=6 rates=invgamma;

	prset applyto=(all) ratepr=variable;
	unlink statefreq=(all) revmat=(all) shape=(all) pinvar=(all) tratio=(all);
END;
```

Now open the nexus file we created, `ConCATenated.nex` in your preferred text editor (or my preferred text editor actually!). As we saw yesterday the data in this format is organized in blocks. The first block is your data, then you will have a block that *Aliview* have created. Something like this:

```

BEGIN ASSUMPTIONS;
EXSET * UNTITLED  = ;
END;

BEGIN CODONS;
CODONPOSSET * CodonPositions =
 N:,
 1: 1-3357\3,
 2: 2-3357\3,
 3: 3-3357\3;
CODESET  * UNTITLED = Universal: all ;
END;

BEGIN SETS;
END;

```

Delete these 2 blocks! We don´t need them. Now replace them with the MrBayes block created by *PartitionFinder*. Save it as `ConCATenatedMB.nex`. We will be using this later. For *IQTree* we don´t need to set the best partitioning scheme as the program will find it as the first step of the analysis. But we would maybe need to create the partition file that can be used to run RaxML on CIPRES for example (We are not going to do so, but you should be able to do it now that you know how *CIPRES* works.).

Take a look again to the result of *PartitionFinder* in your text editor. Look at the block for *RaxML*. It should be something like this:

```
DNA, Subset1 = 1-678\3
DNA, Subset2 = 3359-5175\3, 2-678\3, 2222-3357\3
DNA, Subset3 = 3-678\3, 681-2220\3
DNA, Subset4 = 679-2220\3
DNA, Subset5 = 680-2220\3
DNA, Subset6 = 3358-5175\3, 2221-3357\3
DNA, Subset7 = 3360-5175\3, 2223-3357\3
```

Save this to a new \*.txt file and call it `partitionsCodonPF.txt`. This will be useful for running *RaxML* in *CIPRES* for example.
