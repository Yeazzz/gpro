#GPrO: Generate, Predict and Optimize 3 steps to design artifitial promoters
##Install
'git clone https://github.com/Yeazzz/gpro.git'
##Quick Start
Using over data to quick start Gpro
###Demo 1: Design core promoters of E. coli
Train the generator using  nature E. coli core promoters sequences:
'''
import gpro
generator = gpro.Generator.WGAN()
generator.BuildModel('data/seq_ecoli.txt')
generator.Train()
'''
Train the Predictor

