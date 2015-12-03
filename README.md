
This repository contains information related to the tool ReImInfer presented at Foundations of Software Engineering, 2012. The tool was originally presented in [this paper](http://dl.acm.org.prox.lib.ncsu.edu/citation.cfm?id=2393596.2393640).

This repository _is not_ the original repository for this tool. Here are some links to the original project:
* [The Official Project Page, including source code](https://github.com/proganalysis/type-inference)
* [Link to download the original tool](http://type-inference.googlecode.com/files/type-inference-0.1.2.zip)

In this repository, for ReImInfer you will find:
* :white_check_mark: [Source code (available)](https://github.com/SoftwareEngineeringToolDemos/FSE-2012-ReImInfer)
* :white_check_mark: [Binary (available)](https://github.com/SoftwareEngineeringToolDemos/FSE-2012-ReImInfer/blob/master/type-inference-0.1.2.zip)
* :x: Video of the tool (not available).

This repository was constructed by [Nikhil Chinthapallee](https://github.com/nchinth) under the supervision of [Emerson Murphy-Hill](https://github.com/CaptainEmerson).
Thanks to Wei Huang and Ana Milanova for their help in establishing this repository. 


# Introduction #
  * Extends the [Checker Framework](http://types.cs.washington.edu/checker-framework/)

  * Currently supports inference of Universe Types, Ownership Types, Reference Immutability(reim), EnerJ, SFlow, DFlow and AJ.

  * Download: [issta-artifact-2015.zip](http://www.cs.rpi.edu/~dongy6/issta-artifact-2015/issta-artifact-2015.zip) (144M) contains executable binary, or [issta2015.zip](http://www.cs.rpi.edu/~dongy6/issta-artifact-2015/issta2015.zip) (1.8G) contains executable binary and all benchmarks. NOTE: This is the implementation in the ISSTA'15 paper. Unzip it and follow the instructions in README.

  * Download: [type-inference-0.1.2.zip](http://type-inference.googlecode.com/files/type-inference-0.1.2.zip) contains executable binary and source code. NOTE: It contains  Reference Immutability(reim), Ownership Types, and Universe Types in this zip file. Others will be added soon.

# Installation #
The following instructions assume an Unix-like (e.g Mac, Linux) environment.

**Requirement**: You must have JDK 6 or later installed. The binary release was compiled and tested under JDK 6 on Mac OS X 10.7 and Ubuntu 12.04.

  1. Download [type-inference-0.1.2.zip](http://type-inference.googlecode.com/files/type-inference-0.1.2.zip) and unzip it to create a **type-inference** directory
  1. **Optional** Add type-inference/binary to your PATH
  1. Test if installation is success. Open a command window and change the directory to **type-inference**. Run     `javac -version` if you have added it to your PATH or `./binary/javac` if you didn't, it should output: `javac 1.7.0-jsr308-1.3.0`

# Example use: inferring Reference Immutability and Method Purity #
This is the implementation in the OOPSLA'12 paper.

Suppose that we want to do the inference for one test case included in type-inference-0.1.2.zip: `inference-tests/CellClient.java`.

  1. Change the directory to **type-inference**
  1. Run `./binary/javai-reim inference-tests/CellClient.java`

The inference results are dumped to:
  * new-result.jaif:  The result in JAIF format containing fields, parameters and return values, but no local variables.
  * new-result.csv: The result for all variables.
  * new-pure-methods.csv: The pure methods inferred by the tool.

## Run benchmarks used in the OOPSLA'12 paper ##
  1. Download [2012-oopsla-eval.zip](http://homepages.rpi.edu/~dongy6/2012-oopsla-eval.zip)
  1. Unzip it into two directories: **2012-oopsla-eval** and **benchmarks**
  1. **2012-oopsla-eval** contains scripts for running the benchmarks
  1. **benchmarks** contains all benchmarks used in the paper except SPECjbb.
  1. Please make sure that **JDK 6** is included in your PATH. JDK 7 would cause errors.
  1. Example: execute the script `run-jolden-ri` in **2012-oopsla-eval** to run the benchmark `jolden`

## Use Eclipse Plugin to infer method purity for Java projects ##
  1. Download the [plugin](http://type-inference.googlecode.com/files/ReimInfer_EclipsePlugin.zip) and unzip it into **plugins** folder.
  1. Copy the folder **plugins/edu.rpi.cs.reiminfer\_1.0.0** into your Eclipse plugins folder.
  1. Add the following line in your **eclipse.ini** file: `-Xbootclasspath/p:../../../plugins/edu.rpi.cs.reiminfer_1.0.0/lib/jsr308-all.jar`
  1. In Eclipse, right click a Java project and select **ReimInfer** => **Infer Pure Methods**.

# Build from source code #
  1. Install Oracle JDK 6 and have JAVA_HOME set correctly. JDK 7 and up should be supported but we haven't tested it yet.
  2. Install [Apache Ant](http://ant.apache.org/).
  3. Build jsr308-langtools:
  
  ```bash
  cd type-inference/inference-framework/jsr308-langtools/make
  make
  ```
  4. Build annotation-tools:
  
  ```bash
  cd type-inference/inference-framework/annotation-tools
  ant
  ```
  5. Build annotated JDK:
  
  ```bash
  cd type-inference/inference-framework/checker-framework/checkers/jdk
  make
  ```
   * If you only want to build annotated JDK for some specific type system, please edit Makefile and find the line like:
  
  ```bash
  CHECKER_DIRS = sflow
  ```
  Change sflow to other type system, e.g. reim.
  
  6. Build checkers:
  
  ```bash
  cd type-inference/inference-framework/checker-framework/checkers
  ant bindist
  ```
  Optionally, build checkers without buiding annotated JDK:
  
  ```bash
  ant bindist-nojdk
  ```
  
  7. Test run:
  ```bash
  cd type-inference/inference-framework/checker-framework/checkers
  binary/javai-sflow
  ```

# Instantiation of other type systems #
Note: Inference results for detecting information violations in web apps are available: [webapps-results.tgz](http://www.cs.rpi.edu//~huangw5/webapps-results.tgz). The instantiated inference will be released shortly (available in the source repository).
