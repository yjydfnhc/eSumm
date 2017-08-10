

# ESBM Benchmark 

ESBM (short for Entity Summarization Benchmark) is a dataset for evaluating entity summarization methods (i.e. summarizers). This repository contains data of this benchmark, example outputs of a summarizer, and an evaluator based on this benchmark. 


## Data
The ESBM benchmark consists of information for 140 entities from two datasets (DBpedia and LinkedMDB). For each entity, these information are represented by [N-Triples](https://www.w3.org/TR/n-triples/) documents, and  be categorized into three types:

- `desc`: Entity description;
- `top5`: Ground-truth summary created by crowsourcing with size constraint **k=5**;
- `top10`:  Ground-truth summary created by crowsourcing with size constraint **k=10**;

These files are named by id of the entity (check [elist.txt]() for detailed entity-id list) and postfixed with the file types. Directory structure of these files like the following:

<pre>
|--ESBM_benchmark
	|-- dbpedia
		|-- 1
			|-- 1_desc.nt
			|-- 1_top5.nt
			|-- 1_top10.nt
		|-- 2
		|-- ...
		|-- 100
  	|-- lmdb
		|-- 101
			|-- 1_desc.nt
			|-- 1_top5.nt
			|-- 1_top10.nt
		|-- 102
		|-- ...
		|-- 140
</pre>




## Evaluation

An evaulator written in Java is given for measuring summarizers with the ESBM benchmark. 

### Required Output Format 
Each summary should be represented into a N-Triples file (see [Jena API](http://jena.apache.org/documentation/io/rdf-output.html), or output like [OutputExample](example code)). The folder of output files has similar structure as the benchmark folder, only different in that for each entity, output folder contains the following three files:


- `top5`: Entity summary created by *your summarizer* with size constraint **k=5**;
- `top10`: Entity summary created by *your summarizer* with size constraint **k=10**;
- `rank`: A ranked list of （all) triples from the *desc* file which given as input of your summarizer; This file is optional, and missing this file will make the MAP score be null.

An [example output folder](summ_example) is given in this repository. 

### Run the Evaluator

Before running the evaluator, note that no redundant files are allowed in the output folder;

The evaluator receives two parameters:

- Path of the ESBM benchmark, e.g. `/home/user/eval/ESBM_benchmark`
- Path of your outputs, e.g. `/home/user/eval/summ_example`

Download the `src` folder and build ...


### Representative Summarizers



![F-measure](F-measure.jpg)
![MAP](MAP.jpg)

## Citation

If you use ESBM in your work, please cite:

<pre>
@article{.....,
  author    = {Qingxia Liu and
               Gong Cheng and
               Yuzhong Qu and
               Kalpa Gunaratna},
  title     = {....},
  journal   = {{IEEE} Trans. Knowl. Data Eng.},
}
</pre>

## Acknowledgments
This work was supported in part by the NSFC under Grant 61572247 and 61370019, and in part by the Qing Lan Project.


## Contact



 








