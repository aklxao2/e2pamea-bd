# Extraction of Emerging Patterns through an Adaptive Multi-objective Evolutionary Algorithm (E2PAMEA) & the Bit Look-Up Table (Bit-LUT) chromosome evaluation approach

In this repository the source code of the E2PAMEA and the Bit-LUT algorithms are presented. Please cite this work as:

*Citation not available yet*

## Compile

The algorithm is compiled by means of __sbt assembly__. Assuming sbt is installed in the system, run:

```
sbt assembly
```

## Data format

Data must follows the ARFF dataset format (https://www.cs.waikato.ac.nz/~ml/weka/arff.html).

## Parameters & Execution

The algorithm uses several parameters for its execution. Parameters are speciefied in a Linux-CLI fashion. 
For the execution of the algorithm you must call the "spark-submit" command. The execution CLI line and the list of available commands are presented below (this help is shown in the algorithm when an error is detected or no parameters are added):

```
Usage: spark-submit --master <URL> <jarfile> [-BhvV] [--list] [-e=NUMBER]
                                             [-i=NUMBER] [-l=NUMBER]
                                             [-n=STRING] [-p=NUMBER] [-r=PATH]
                                             [-s=SEED] [-t=PATH] [-T=PATH]
                                             [-f=FILTER,THRESHOLD[,FILTER,
                                             THRESHOLD...]]... [-o=OBJ[,
                                             OBJ...]]... trainingFile testFile

Fast Big Data MOEA

      trainingFile           The training file in ARFF format.
      testFile               The test file in ARFF format.
  -B, --bigdata              If set, the evaluation in the evolutionary process is
                               performed on the optimised BitSet structure by means
                               of an RDD. This means that for each generation, a
                               MapReduce procedure is triggered for evaluating the
                               individuals. RECOMMENDED FOR VERY BIG DATA SETS.
  -e, --evaluations=NUMBER   The maximum number of evaluations until the end of the
                               evolutionary process.
  -f, --filter=FILTER,THRESHOLD[,FILTER,THRESHOLD...]
                             The filter by measure to be applied. The format must be
                               MEASURE,THRESHOLD, where MEASURE is one of the
                               available quality measures. By default a confidence
                               filter with a threshold=0.6 is applied
  -h, --help                 Show this help message and exit.
  -i, --individuals=NUMBER   The number of individuals in the population
  -l, --labels=NUMBER        The number of fuzzy linguistic labels for each variable.
  -n, --null=STRING          A string that represents null values in the datasets.
                               By default it is '?'
  -o, --objectives=OBJ[,OBJ...]
                             A comma-separated list of names for the quality
                               measures to be used as optimisation objectives.
  -p, --partitions=NUMBER    The number of partitions used within the MapReduce
                               procedure
  -r, --rules=PATH           The path for storing the rules file.
  -s, --seed=SEED            The seed for the random number generator.
  -t, --training=PATH        The path for storing the training results file.
  -T, --test=PATH            The path for storing the test results file.
  -v                         Show Spark INFO messages.
  -V, --version              Print version information and exit.
      --list                 List the quality measures available to be used as
                               objectives.

```


## Artificial datasets employed.

A set of artificial datasets were generated in this study in order for determining the scalability of the proposal. In this section the details of the datasets are presented for replication purposes.

The datasets were generated by MOA [(https://moa.cms.waikato.ac.nz/)](https://moa.cms.waikato.ac.nz/). Using MOA, the commands employed for generating the datasets of the study were the following:

### Scalability on the number of instances

```
WriteStreamToARFFFile -s (generators.RandomTreeGenerator -r 1 -o 10 -u 10) -f (ArtInstances_x.arff) -m 100000000
```


### Scalability on the number of variables

```
WriteStreamToARFFFile -s (generators.RandomTreeGenerator -r 1 -o 50 -u 50) -f (ArtVariables_x.arff) -m 1000000
WriteStreamToARFFFile -s (generators.RandomTreeGenerator -r 1 -o 250 -u 250) -f (ArtVariables_x.arff) -m 1000000
WriteStreamToARFFFile -s (generators.RandomTreeGenerator -r 1 -o 500 -u 500) -f (ArtVariables_x.arff) -m 1000000
WriteStreamToARFFFile -s (generators.RandomTreeGenerator -r 1 -o 2500 -u 2500) -f (ArtVariables_x.arff) -m 1000000
WriteStreamToARFFFile -s (generators.RandomTreeGenerator -r 1 -o 5000 -u 5000) -f (ArtVariables_x.arff) -m 1000000
WriteStreamToARFFFile -s (generators.RandomTreeGenerator -r 1 -o 7500 -u 7500) -f (ArtVariables_x.arff) -m 1000000
```

