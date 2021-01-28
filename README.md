# Cheat-Sheet

**Tutorials**

[Snakemake](https://slowkow.com/notes/snakemake-tutorial/)

**LOAD project paths**
```
/sc/arion/projects/LOAD/shea/
/sc/arion/projects/LOAD/shea/bin/MitoImpute
/sc/arion/projects/LOAD/shea/Projects/MR_ADPhenome/
/sc/arion/projects/LOAD/shea/data/sumstats_munger
/sc/hydra/scratch/andres12
```

**tmux**
```
tmux new -s myname
tmux a -t myname
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

```
#!/bin/bash
#BSUB -J "Job Name"
#BSUB -P acc_load
#BSUB -q premium
#BSUB -n 2
#BSUB -R span[hosts=1]
#BSUB -R rusage[mem=16000]
#BSUB -W 24:00
#BSUB -oo %J.stdout
#BSUB -eo %J.stderr

"Command"
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
scp /Users/shea/Downloads/file andres12@chimera.hpc.mssm.edu:/sc/arion/projects/LOAD/shea/file 
```

**Launch interactive job**
```
bsub -P acc_LOAD -q premium -R span[hosts=1] -R rusage[mem=4000] -W 140:00 -n 8 -Is /usr/bin/env bash
```

[](https://stackoverflow.com/questions/25721884/how-should-i-deal-with-package-xxx-is-not-available-for-r-version-x-y-z-wa)

## Just reformated a computer, now what 

### Computing 

* [Atom](https://atom.io/)
  - rbox
  - pigments
  - minimap-pigments
  - minimap-linter
  - minimap-find-and-replace
  - minimap-lens
  - minimap-split-diff
  - split-diff
  - teletype
  - sublime-style-column-selection
  - blame
  - file-icons
  - git-plus
  - git-control 
  - git-history
  - language-markdown
  - language-fish-shell
  - linter-tidy
* [iTerm2](https://iterm2.com/downloads.html)
* [R](https://cran.r-project.org/bin/macosx/)
* [Rstudio](https://rstudio.com/products/rstudio/download/)
* [Homebrew](https://brew.sh/)
  - [Git](https://git-scm.com/download/mac): `brew install git`
  - [Fish](https://fishshell.com/): 'brew install fish'
* [Oh my fish](https://github.com/oh-my-fish/oh-my-fish): `curl -L https://get.oh-my.fish | fish`
  - `omf install jacaetevha; omf theme jacaetevha`
* [Miniconda](https://conda.io/en/latest/miniconda.html)
* [Snakemake](https://snakemake.readthedocs.io/en/stable/getting_started/installation.html)
* [macFuse & sshfs](https://osxfuse.github.io/)

### Software 
* [Google Chorme](https://www.google.com/chrome/)
* [Dropbox](https://www.dropbox.com/downloading)
* [Microsoft 365](https://www.office.com/)
  - Outlook: Exchange; Username: MSSMCAMPUS\username; pwd
* [Zoom](https://zoom.us/download)

### App Store
* [iStat Menues](https://apps.apple.com/us/app/istat-menus/id1319778037?mt=12)
* [tadam](https://apps.apple.com/us/app/tadam-stay-focused-at-work/id531349534?mt=12)

**ssh & sshfs**

create ssh/config and dir 

```
vim ~/.ssh/config
mkdir ~/.ssh/cm_socket
chmod 700 ~/.ssh/cm_socket
```

for sshfs 
Make root directories [guide](https://derflounder.wordpress.com/2020/01/18/creating-root-level-directories-and-symbolic-links-on-macos-catalina/)
```
sudo touch /etc/synthetic.conf
sudo vim /etc/synthetic.conf
# add to /etc/synthetic.conf symlinks to root dir (rm comments)
# sc	/Users/sheaandrews/minerva_sc
# hpc	/Users/sheaandrews/minerva_hpc
chmod 644 /etc/synthetic.conf
```

create mc script. 
```
vim /Users/sheaandrews/.local/scripts/mc
```

set permisions 
```
sudo dscl . -create /Groups/LOAD
sudo dscl . -create /Groups/LOAD gid 31387
sudo dscl . -create /Groups/LOAD GroupMembership $USER
```

**Config files** 

```
vim ~/.bashrc
vim ~/.config/fish/config.fish
```


