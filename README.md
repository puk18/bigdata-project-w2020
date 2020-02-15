# bigdata-project-w2020
# Code Clone Detection

Abstract 

Large program code has little or no comments that leads to problems in code comprehension,the better approach is when comments would be generated automatically on the basis of mining stack overflow which contains code-description mappings. However for mapping these descriptions to unknown codes we need to detect code clones i.e similar code segments.There are 4 types of code clones and various approaches for detecting code clones such as lexical parsing and also generating abstract syntax trees and program dependency graphs. These approaches will be used to generate features which will then be used to train our classification algorithms using scikit learn.  


1.Introduction

Code clones are two fragments of codes which are identical to each other which are generated using copy and paste activities of the programmer, but the main problem with code clones is replication of bugs and difficulties in software comprehension and maintenance, so it becomes imperative to detect these clones.The 4 types of clones are:
Type1 clones:-These are Identical code fragments but may have some variations in whitespace, layout, and comments 
Type2 clones:-These are Syntactically equivalent fragments with some variations in identifiers names, literals, types, whitespace, layout and comments 
Type3 clones:-These are also Syntactically similar code with inserted, deleted, or updated statements 
Type4 clones:-These are  Semantically equivalent, but syntactically different code 

Initially we are working on detecting type1 and type 2 clones and will further extend our work on detecting type 3 and type 4 clones. For detecting type 1 and type 2 clones we will perform lexical analysis  of the source codes. Lexical analysis will help in assigning special tokens(i.e identifiers,constants,operators etc) to code present in source files.

We will use these special tokens as features i.e number of identifiers, constants, keywords etc present in the program. If the other code has similar number of these tokens these codes may be similar

For eg. Consider two simple java program to add two numbers :

![GitHub Logo](/images/logo1.jpg)
Format: ![Alt Text](url)



As we can see these lexical analysis outputs for these two programs are completely similar even though they are syntactically different, we will use these lexical tokens as features for our classifiers.

There have been works to detect code clones but however most of the work has been done using text-based techniques[1] which are good to detect type 1 clones,people have also worked upon token based,syntax trees[2] or graph based detection techniques but very have used machine learning to detect clones[3][4]. 




2.Materials and Methods 

As discussed above we will generate our dataset with the help of lexical analyser from various various source codes written in java,These dataset of source codes is IJaDataset, it has variety of source codes which will be used to generate tokens.This IJADataset contains around  47885 with    1009k lines of code.

For generating lexical tokens initially we thought of building our own lexical analyser however it will be time consuming and some off the shelf components already exist so we are using an already available lexical analyser known as Jflex.This tool will take as input the source code and generate the lexical tokens for source code, these lexical tokens will be stored in a .csv file such that each row in .csv file would represent different number of token present in each source code file.


![GitHub Logo](/images/logo.jpg)
Format: ![Alt Text](url)








 Proposed Work
   
		 	 	 		
Initially we are dealing with the classification problem our labels will include the type of code i.e if it’s a sorting code so it will have a label as filename which will then be used to check with the files in testing,If a file in testing would have same features then it will detect the clone and output the name of identical code fragment in the training set.Further more we are planning to also perform clustering such that it will group similar codes in the same group.

Random forest, SVM(Support Vector Machine) algorithm will be used for classification and for clustering K-means algorithm will be used.We will use the scikit implementation of these algorithms.

Random Forest: Random forest is basically a combination of decision trees. Instead of simply averaging the prediction of trees, this model is based on the following factors because of which we call it a random forest. The factors are:
Random sampling of training data points while building trees
Random subsets of features considered while splitting nodes

When we train each tree in a random forest, each tree learns from a random sample of data points. In a similar fashion, the other trees are trained and at the end the average of predictions is calculated to get the averaged prediction, This process is also termed as bagging.Also, while splitting the individual nodes in each decision tree, we only consider the subset of features and again at the end, the average is calculated to get the prediction.

SVM: SVM(Support Vector Machine) is the differentiating classifier which is used for linear and non linear data and it is defined by a type of separation called hyperplane. This method is supported by a labeled training data set which is supervised and the algorithm gives the output in the form of hyperplane which differentiates new examples. Hyperplane is a new dimension which seeks for optimal separation so called decision boundary. The core idea behind this algorithm is to separate the data from two different classes in the fashion of a hyperplane.  Usually there are an infinite number of lines i.e. hyperplanes that separates two classes but this algorithm aims to minimize the classification error and it searches the hyperplane that has the maximum margin known as maximum marginal hyperplane(MMH)
	
References:
1. Roy, Chanchal K., and James R. Cordy. “NICAD: Accurate detection of near-miss intentional clones using flexible pretty-printing and code normalization.” Program Comprehension, ICPC. The 16th IEEE International Conf. on. IEEE, 2008.
1. Baxter, Ira D., et al. “Clone detection using abstract syntax trees.” Software Maintenance, Proc. , Int.l Conf. on. IEEE, 1998. .
1. Code clones detection using machine learning technique: Support vector machine.https://ieeexplore.ieee.org/document/7813733
1. Semantic Clone Detection Using Machine Learning https://ieeexplore.ieee.org/document/7838289

