# Cheat-Sheet

**LOAD project paths**
```
/sc/arion/projects/LOAD/shea/
/sc/arion/projects/LOAD/shea/bin/MitoImpute
/sc/arion/projects/LOAD/shea/Projects/2_MR/
/sc/arion/projects/LOAD/shea/data/sumstats_munger
/sc/hydra/scratch/andres12
```

**sshfs**
```
sshfs andres12@bode.hpc.mssm.edu:/sc/orga/projects/LOAD ~/LOAD_minerva/dummy
```

**Moving binary file to be able to launch from anywhere**
```
cp <binary.file> /usr/local/bin/
```

**Use Awk to find the max value in a column**

Find the highest value in column 1, skipping the header, print the whole line. 
```
awk -v max=0 'FNR > 1 {if($1>max){want=$0; max=$1}}END{print want} ' file
```

**Delet all stdout and stderr files in a directory**
```
find . -name "*stdout" -type f -delete
find . -name "*stderr" -type f -delete
```

**bsub job submission**
```
bsub -J "job name" -P acc_load -q premium -n 1 -R span[hosts=1] -R rusage[mem=16000] -W 24:00 -L /bin/bash \
-o jobname.stdout -eo jobname.stderr "command"
```

**Number of jobs running** 

```
runningJobs=$(bjobs | grep RUN | wc -l); TotalJobs=$(bjobs | wc -l); bjobs -w; echo "Currently ${runningJobs} out of ${TotalJobs} are running"
```

**Decompress .bgz file** 

```
mv file.vcf.bgz file.gz
```

**Fine file name in directory** 

```
find | grep "string"
```

**SCP from chimera to local**

```
scp andres12@chimera.hpc.mssm.edu:/sc/orga/projects/LOAD/shea/file /Users/shea/Downloads/
```

**SCP from local to chimera**

```
scp /Users/shea/Downloads/file andres12@chimera.hpc.mssm.edu:/sc/orga/projects/LOAD/shea/file 
```

**Launch interactive job**
```
bsub -P acc_LOAD -q premium -R span[hosts=1] -R rusage[mem=4000] -W 140:00 -n 8 -ISs /usr/bin/env bash
```
