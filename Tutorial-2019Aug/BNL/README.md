### Running the tutorial example at BNL Tier3

#### Login to BNL machines
First you need ssh to spar machines at BNL:
```shell
$ ssh -Y atlasgw
$ rterm -i
```
#### Location of this analysis example package at BNL
You can pull the analysis package under the same github repo directory or copy from the directory at BNL:

```
/atlasgpfs01/usatlas/data/yesw2000/T3-Example-BNL/
|-- 00-Readme.txt
|-- Condor-Job
|   `-- test-condor.job
`-- src
    |-- CMakeLists.txt
    `-- Exam_JetsPlot.cxx
```

where you can find:
- the text instruction file **00-Readme.txt**, from which you can copy/paste the commands used in this tutorial.
- The condor job description file **test-condor.job**
- And the source code of this analysis pacakge under subdir **src/**


#### Setup of the Release Env
First set up the env:
setupATLAS
asetup AnalysisBase,21.2.81
Next time you log in, you can simply run "asetup" under that dir.

