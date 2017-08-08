# eSumm



To evaluate your solution with the ESBM benchmark, please do the following steps:
1. Download the ESBM benchmark data and package of the Evaluator. (here)
2. Output your results into NT files (each summary in a file). 
These files should be organized as the following folder structure (or see the example).
--algoSummDir
	|-- dbpedia
		|-- 1
			|-- 1_top5.nt
			|-- 1_top10.nt
			|-- 1_rank.nt
		|-- 2
		|-- ...
		|-- 100
  	|-- lmdb
		|-- 101
			|-- 1_top5.nt
			|-- 1_top10.nt
			|-- 1_rank.nt
		|-- 102
		|-- ...
		|-- 140

Note that:
(1) No redundant files are allowed in this folder;
(2) "xx_rank.nt" files are optional, each of these files give a ranked list of (all) triples from an entity description. 
Missing these files will make the MAP score be null. 
		
		
3. Run the evaluator. 
The evaluator receives two inputs:
(1) the path of the ESBM benchmark, e.g. /home/user/ESBM
(2) The path of your results, e.g. /home/user/algoSummDir
You could run the evaluator using the following command:

java -jar evaluator.jar /home/user/ESBM /home/user/algoSummDir

(Before running the evaluator, make sure that you already have installed the Java environment. Tips for )

4. Report the output of evaluator.
The output of the evaluator for our example data will be:
dbpedia@top5:	F=0.2493, MAP=0.3115912129252924
dbpedia@top10:	F=0.46826666666666644, MAP=0.463081836461084
lmdb@top5:	F=0.211, MAP=0.29833952642671263
lmdb@top10:	F=0.2595833333333334, MAP=0.4179389782056087

where F=0.2493 represents the average F-measure score of your "_top5.nt" files for dbpedia entities with respect to the ground truth for k=5;
MAP=0.3115912129252924 means the MAP score of your "_rank.nt" files for dbpedia entities with respect to the ground truth for k=5;




