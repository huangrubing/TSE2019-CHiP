# CHiP
Configurable Hybrid Parallel Covering Array Constructor

**Configuration Space Model File**
* Configuration space models have the .configModel extension.
* Input explanations for each line of the file:
  1) Name of the output file for the computed covering array.
  2) Experiment id. This id is used for automated testing. 
  3) Number of options. Option enumeration starts with 0, i.e., first option is the 0th option.
  4) Number of values for each option can take. Value enumeration for an option starts with 0. 
  5) Number of constraints. Constraints are defined as invalid tuples. A group of invalid tuples may infer new invalid tuples a.k.a. implicit invalid tuples. Our tool identifies implicit invalid tuples and report the minimal number of invalid tuples (for detailed explanation, see paper). Therefore, in the final report, the number of constraints may differ from the one given in configuration space model file.
  Following from 5th line of the file,  the constraints are described if there exist any. Each consecutive 2 lines indicate a single constraint. First line is the length of the constraint, and the next line is the constraint itself. They are ordered as option and values pairs. For example, consider that 2 constraints are given as follows.

  2  
  1 0 2 1  
  3  
  2 2 1 1 5 0  
  
  They indicate that the tuples (o1=0∧o2=1) and (o2=2∧o1=1∧o5=0) are forbidden to be appear in any configurations of computed covering array, i.e., they are invalid tuples.
* A sample configuration space model as well as a set of configurations space models for benchmarking are provided.
* Currently CHiP supports 3 different strength values, t=2, 3 and 4.
* All the experiment results reported in the paper are presented in the Experiments folder.

**Dependencies**
* CUDA programming model, https://developer.nvidia.com/. We tested CHiP with CUDA 7.5, therefore any version aobve that should be enough. 
* Sugar: a SAT-based Constraint Solver, http://bach.istc.kobe-u.ac.jp/sugar/
* ACTS v2.9: https://csrc.nist.gov/projects/automated-combinatorial-testing-for-software/
* GECODE: http://www.gecode.org/
  
**How to build**
* Currently we do not provide the source code.

**How to run**
./CHiP -c chipVersion -t 3 -m /path/to/configModel -a /path/to/acts -s /path/to/sugar

* -c : CHIP configuration. Available parameters are: f, b, q and sq. Default is b. 
* -t : Strength of the covering array. 
* -m : Path to configuration space model file. 
* -a : Path to acts.jar file. 
* -s : Path to sugar file. 

An example run:    
> ./CHiP -c b -m sample.configModel -a actsPath -s sugarPath -t 3


Note: This is the first release of the tool, so please send any errors that you encounter or any suggestions and questions about the tool to hanefimercan@sabanciuniv.edu

The paper about CHiP is currently under review, therefore we can not give detail about the algorithm and share the source code of the CHiP for the moment.
