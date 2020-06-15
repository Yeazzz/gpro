# GPrO: Generate, Predict and Optimize 3 steps to design artifitial promoters
## Install
`git clone https://github.com/Yeazzz/gpro.git`
## Quick Start
Using over data to quick start Gpro
### Demo 1: Design core promoters of E. coli
In our previous research *Synthetic promoter design in Escherichia coli based on a deep generative network*, we designed artifitial promoters which had successfully expressed in E. coli. Using **Gpro** can easily reappear our result.

Train the generator using  nature E. coli core promoters sequences:
```
import gpro
generator = gpro.Generators.WGAN()
generator.BuildModel('data/seq_ecoli.txt')
generator.Train()
```
Generate promoter sequences:
```
import numpy as np
N = 100000000 # the number of sequences to generate
seq = generator.Generator(np.random.normal(size=(N,generator.Z_DIM) ))
```
Train the Predictor using E. coli expression data:
```
predictor = gpro.Predictors.CNN()
predictor.BuildModel('data/exp_ecoli.txt')
predictor.Train()
```
Predict the expression of artifitial promoters:
```
exp = predictor.Predictor(seq)
```
Filter the Top 100 expression to experiment：
```
I = np.argsort(exp)
I = I[::-1] # in descending order of expression
seqout = seq[I[:100]]
```

