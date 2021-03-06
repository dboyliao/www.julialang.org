---
layout: insidepage
title: Data Science and Machine Learning Projects – Summer of Code
---

Note that for any of these projects you should have code samples as part of your application, ideally as patches to one of the ML or GPU libraries or in the form of working ML models.

## NLP Tools and Models

Build deep learning models for Natural Language Processing in Julia. [TextAnalysis](https://github.com/juliatext/TextAnalysis.jl)  and [WordTokenizers](https://github.com/JuliaText/WordTokenizers.jl) contains the basic algorithms and data structures to work with textual data in Julia. On top of that base, we want to build modern deep learning models based on recent research. This project will need familiarity with [Flux](http://fluxml.ai) and deep learning concepts. The following tasks can span multiple students and projects. 

* Implement BERT in Julia
* Implement ELMo in Julia
* Implement practical models for sentiment analysis, part of speech (POS) tagging, named entity recognition (NER), classification and parsing
* Test and validate these models

**Mentors**: [Avik Sengupta](https://github.com/aviks/) & [Lyndon White](https://github.com/oxinabox/)

## Model Zoo Examples

[Flux](https://github.com/FluxML/Flux.jl)'s [model zoo](https://github.com/FluxML/model-zoo/) contains examples of a wide range of deep learning models and techniques. This project would involve adding new models, showing how to recreate state-of-the-art results (e.g. AlphaGo) or interesting and unusual model architectures (e.g. transformer networks). We'd be particularly interested in any models involving reinforcement learning, or anything with images, sound or speech.

Some experience with implementing deep learning models would be ideal for this project, but is not essential for a student willing to pick up the skills and read ML papers. It's up to you whether you implement a single ambitious model, or multiple small ones. A good source of inspiration might be the [NIPS Challenge](https://nurture.ai/nips-challenge).

**Mentors**: [Mike Innes](https://github.com/MikeInnes/)

## Flux.JS demos

[Flux.JS](https://github.com/FluxML/FluxJS.jl) enables export of [Flux](https://github.com/FluxML/Flux.jl) models to the browser. However, just porting a numerical function to JavaScript is rarely exciting on its own; you need to build an interface to give input to the model (say, via a webcam) and see output (say, by displaying an annotated image) in order to see what the model is thinking.

This project would involve creating new demos that show interesting models running in the browser. Examples could include:

* An MNIST digit classify running on hand-drawn images;
* [Handwriting generation](https://www.cs.toronto.edu/~graves/handwriting.html);
* Live speech recognition or production;
* An autoencoder that allows moving sliders to generate images, and explore "digit space";
* A Chess or Go AI that plays against the user;
* A language analysis tool that classifies user-written text.

The possibilities are pretty much endless here. This project will require a pretty solid handle on web technologies, and we'd expect much of the components created to be reusable between demos.

**Mentors**: [Mike Innes](https://github.com/MikeInnes/), [Shashi Gowda](https://github.com/shashi).

## Model Import and Export

Sharing models with other frameworks would enable us to both export models (say to JavaScript for the browser, or TensorFlow Lite for mobile, or NNVM for optimised training) and to take advantage of the large set of [trained models in the wild](https://github.com/BVLC/caffe/wiki/Model-Zoo) in Julia code.

This involves several stages, some or all of which could be tackled over the course of a project.

* Reading and writing the raw model formats. For formats like [ONNX](https://github.com/onnx/onnx) this should be relatively easy, as one can use the [ProtoBuf.jl](https://github.com/JuliaIO/ProtoBuf.jl) library.
* For model import:
  * Converting the raw model format to a more general graph format, such as a [DataFlow.jl](https://github.com/MikeInnes/DataFlow.jl) graph.
  * Dumping the model graph as Julia code.
* For model export:
  * Converting a general graph format to the raw model constructs.
  * Tracing Julia code to produce a dataflow graph, as in [FluxJS.jl](https://github.com/FluxML/FluxJS.jl).

**Mentors**: [Mike Innes](https://github.com/MikeInnes/)

## Benchmarks

A benchmark suite would help us to keep Julia's performance for ML models in shape, as well as revealing opportunities for improvement. Like the model-zoo project, this would involve contributing standard models that exercise common ML use case (images, text etc) and profiles them. The project could extend to include improving performance where possible, or creating a "benchmarking CI" like Julia's own [nanosoldier](https://github.com/JuliaCI/Nanosoldier.jl).

**Mentors**: [Mike Innes](https://github.com/MikeInnes/)

## Compiler Optimisations

Julia opens up many interesting opportunities for applying new optimisations to ML models, and exploring [language design for ML](https://julialang.org/blog/2017/12/ml&pl). As part of this project you'd help us apply novel optimisation strategies to Julia code, with immediate benefits to Flux and other Julia users.

Possible projects could include:

* Auto-parallelisation and vectorisation in the vain of [DyNet autobatch](http://dynet.readthedocs.io/en/latest/tutorials_notebooks/Autobatching.html), [TensorFlow Fold](https://github.com/tensorflow/fold) and [Matchbox](https://github.com/jekbradbury/Minibatch.jl).
* Using [Cassette](https://github.com/jrevels/Cassette.jl/) and techniques similar to [Flux.JS](https://github.com/FluxML/FluxJS.jl) to extract dataflow computation graphs from imperative Julia code.
* Applying optimisations to computation graphs, such as eliding memory allocations, reusing memory and fusing operations, or enabling model parallelism.
* Applying [Halide](http://halide-lang.org/) or [Futhark](https://futhark-lang.org/)-like optimisations to array expressions, as in [Tokamak](https://github.com/MikeInnes/Tokamak)
* Improving Julia's GPU support, including tuning memory management and supporting CUDA streams.

**Mentors**: [Mike Innes](https://github.com/MikeInnes/)

## Sparse GPU and ML support

While Julia supports dense GPU arrays well via [CuArrays](https://github.com/JuliaGPU/CUSPARSE.jl), we lack up-to-date wrappers for sparse operations. This project would involve wrapping CUDA's sparse support, with [CUSPARSE.jl](https://github.com/JuliaGPU/CUSPARSE.jl) as a starting point, adding them to CuArrays.jl, and perhaps demonstrating their use via a sparse machine learning model.

**Mentors**: [Mike Innes](https://github.com/MikeInnes/)



## Parquet.jl enhancements

Efficient storage of tabular data is an important component of the data analysis story in the ecosystem. Julia has many options here -- JLD, JuliaDB’s built-in serialization, CSV.write. These either suffer from lack of performance or lack of standardization. Parquet is a format for efficient storage of tabular data used in the Hadoop world. It has compression techniques which reduce disk usage as well as speed up reads. A well-rounded Parquet implementation in Julia will solve the current issues with storage formats and let Julia interoperate with software from the Hadoop world.

Parquet.jl currently contains a reader for Parquet files. This project involves implementing the writer for Parquet files, as well as some enhancements to the reading functionality.

**Deliverables:**

_Reader enhancements:_

Read a file as a NamedTuple of vectors (using NamedTuples.jl on Julia 0.6). This is on similar lines, but different from the current cursor-based reader. Probably as an implementation of `AbstractBuilder` that returns NamedTuple of column vectors, combined with a new iterator/cursor that returns a bunch of records instead of individual records.

_Writer support:_

- Write a table (in the form of a NamedTuple of vectors) to disk.
  Note: we will use NamedTuple of vectors as a minimal table which can be converted back into DataFrames or IndexedTables
- Implement the compression features provided in the Parquet spec-
Optionally auto detect compression scheme based on the data.

**Mentors**: [Tanmay Mohapatra](https://github.com/tanmaykm)

## GPU support in JuliaDB

JuliaDB is a distributed analytical database. It uses Julia’s multi-processing for parallelism at the moment. GPU implementations of some operations may allow relational algebra with low latency. In this project, you will be required to add basic GPU support in JuliaDB.

- Copy a table to GPU -- this may be as simple as converting every column into a CuArray or GPUArray
- `map`, `reduce` and `filter` operation -- apply simple functions on a large table that is on the GPU
  - Ensure that columnar storage format is made use of in the lower level code generated.
- The `groupby` and `join` operations may involve first implementing an efficient [`sortperm`](https://docs.julialang.org/en/v1/base/sort/#Base.sortperm) that utilize the GPU, or an efficient hash table on the GPU
- `groupby` kernel on GPU
- `join` kernel on GPU (stretch goal)

**Mentors**: [Shashi Gowda](https://shashi.github.io), [Mike Innes](http://mikeinnes.github.io/)


## Accelerating optimization via machine learning with surrogate models

In many cases, when attempting to optimize a function `f(p)` each calculation
of `f` is very expensive. For example, evaluating `f` may require solving a
PDE or other applications of complex linear algebra. Thus, instead of always
directly evaluating `f`, one can develop a surrogate model `g` which is
approximately `f` by training on previous data collected from `f` evaluations.
This technique of using a trained surrogate in place of the real function
is called surrogate optimization and mixes techniques from machine learning
to accelerate optimization.

Advanced techniques [utilize radial basis functions](https://www.cambridge.org/core/journals/acta-numerica/article/kernel-techniques-from-machine-learning-to-meshless-methods/00686923110F799A1537C4F02BBAAE8E) and Gaussian
processes in order to interpolate to new parameters to estimate `f` in areas
which have not been sampled. [Adaptive training techniques](http://www.ressources-actuarielles.net/EXT/ISFA/1226.nsf/9c8e3fd4d8874d60c1257052003eced6/e7dc33e4da12c5a9c12576d8002e442b/$FILE/Jones01.pdf) explore how to pick new areas
to evaluate `f` to better hone in on global optima. The purpose of this project
is to explore these techniques and build a package which performs surrogate
optimizations.

**Recommended Skills**: Background knowledge of standard machine learning,
statistical, or optimization techniques. Strong knowledge of numerical analysis
is helpful but not required.

**Expected Results**: Library functions for performing surrogate optimization
with tests on differential equation models.

**Mentors**: [Chris Rackauckas](https://github.com/ChrisRackauckas)

## Parameter estimation for nonlinear dynamical models

Machine learning has become a popular tool for understanding data, but scientists
typically understand the world through the lens of physical laws and their
resulting dynamical models. These models are generally differential equations
given by physical first principles, where the constants in the equations such
as chemical reaction rates and planetary masses determine the overall dynamics.
The inverse problem to simulation, known as parameter estimation, is the process
of utilizing data to determine these model parameters.

The purpose of this project is to utilize the growing array of statistical,
optimization, and machine learning tools in the Julia ecosystem to build
library functions that make it easy for scientists to perform this parameter
estimation with the most high-powered and robust methodologies. Possible projects
include improving methods for Bayesian estimation of parameters via Stan.jl
and Julia-based libraries like Turing.jl, or global optimization-based approaches.
Novel techniques like classifying model outcomes via support vector machines
and deep neural networks is can also be considered. Research and benchmarking
to attempt to find the most robust methods will take place in this project.
Additionally, the implementation of methods for estimating structure, such
as [topological sensitivity analysis](http://www.pnas.org/content/111/52/18507)
along with performance enhancements to existing methods will be considered.

Some work in this area can be found in
[DiffEqParamEstim.jl](https://github.com/JuliaDiffEq/DiffEqParamEstim.jl)
and [DiffEqBayes.jl](https://github.com/JuliaDiffEq/DiffEqBayes.jl). Examples
can be found [in the DifferentialEquations.jl documentation](http://docs.juliadiffeq.org/latest/analysis/parameter_estimation.html).

**Recommended Skills**: Background knowledge of standard machine learning,
statistical, or optimization techniques. It's recommended but not required that
one has basic knowledge of differential equations and DifferentialEquations.jl.
Using the differential equation solver to get outputs from parameters can
be learned on the job, but you should already be familiar (but not necessarily
an expert) with the estimation techniques you are looking to employ.

**Expected Results**: Library functions for performing parameter estimation
and inferring properties of differential equation solutions from parameters.
Notebooks containing benchmarks determining the effectiveness of various methods
and classifying when specific approaches are appropriate will be developed
simultaneously.

**Mentors**: [Chris Rackauckas](https://github.com/ChrisRackauckas)

## Artificial Intelligence Library Package based on Artificial Intelligence - A Modern Approach (AIMA)

AIMA is a seminal text on representation of agents to solve AI problems. Most packages
available today as AI libraries tend to focus on ML only and not the architectural
aspect of AI. The scope of the project is to create a library with a clean API
(following AIMA) to easily allow the application of core algorithms to AI problems.
The student will implement a package that brings together implementations of algorithms
like depth-first search and simulated annealing, both from other Julia packages and
from sample code in the AIMA book, and build sample programs to demonstrate AI
applications. Starter code can be found at [AIMACore]
(https://github.com/sambitdash/AIMACore.jl) along with [AIMASamples]
(https://github.com/sambitdash/AIMASamples.jl).

**Recommended Skills**: Previous experience with AI or the ability to quickly pick up on
the AI algorithms in AIMA

**Expected Results**: A well-documented library of functions derived from the AIMA book.

**Mentors** [Sambit Kumar Dash](https://github.com/sambitdash).

## A SQL backend for Query.jl

[Query.jl](https://github.com/davidanthoff/Query.jl) is designed to work
with multiple backends. This project would add a SQL backend, so that queries
that are formulated with the query commands in [Query.jl](https://github.com/davidanthoff/Query.jl)
get translated into an equivalent SQL query that can be run within a
SQL database engine. Both LINQ and dplyr support a similar feature set,
and this project would enable the same scenario for julia. There is also
a small academic literature on this topic that we need to understand and
incorporate.

**Recommended Skills**: Very strong database and SQL skills, previous
experience with compilers (this project is essentially a compiler that
translates a query AST into SQL) and a strong familiarity with the julia
data stack.

**Expected Results**: A new version of [Query.jl](https://github.com/davidanthoff/Query.jl)
that runs queries as SQL in a database.

**Mentors**: [David Anthoff](https://github.com/davidanthoff)

## Tabular file IO

The Queryverse has a large number of file IO packages: [CSVFiles.jl](https://github.com/davidanthoff/CSVFiles.jl),
[ExcelFiles.jl](https://github.com/davidanthoff/ExcelFiles.jl), [FeatherFiles.jl](https://github.com/davidanthoff/FeatherFiles.jl),
[StatFiles.jl](https://github.com/davidanthoff/StatFiles.jl), [ParquetFiles](https://github.com/davidanthoff/ParquetFiles.jl)
and [FstFiles.jl](https://github.com/davidanthoff/FstFiles.jl). This project
will a) do serious performance work across all of the existing packages and
b) add write capabilities  to a number of them.

**Recommended Skills**: Experience with file formats, writing performant
julia code.

**Expected Results**: Write capabilities across the packages listed above,
competitive performance for all the packages listed above.

**Mentors**: [David Anthoff](https://github.com/davidanthoff)
