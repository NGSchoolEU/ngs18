# NGSchool2018 materials

Materials prepared by the instructors of the [#NGSchool2018](https://ngschool.eu/2018). 

You can sync all data using (**don't do it during workshops!**):
```bash
rsync -avz --exclude="*.git/" USERNAME@192.168.1.111:/ngschool/2018 ~/ngschool
# and type your password
```

**Table of Contents**  
   * [NGSchool2018 materials](#ngschool2018-materials)
      * [Dependencies](#dependencies)
      * [Running exercises](#running-exercises)
         * [Working in your own laptop](#working-in-your-own-laptop)
         * [Working in remote NGSchool server](#working-in-remote-ngschool-server)
         * [Working in VirtualBox](#working-in-virtualbox)
      * [Cloning the repository](#cloning-the-repository)
         * [Materials not included in github repo](#materials-not-included-in-github-repo)


## Dependencies
In order to run workshop examples in your own laptop, you'll need to install all below prerequesities.  
**Note, the installation instructions are meant for Ubuntu 18.04. 
Everything should be done in below order, it may take a few hours (especially compilation of R packages is lengthy...)
and around 15-20GB of hard-drive space.**

### Ubuntu
```bash
sudo apt install htop git python3-pip
```

### PIP3
```bash
# albacore ie. read_fast5_basecaller.py + all dependencies
sudo pip3 install 2018/src/whl/ont_albacore-2.3.3-cp36-cp36m-manylinux1_x86_64.whl 
```

### R, Bioconductor and other R packages
```bash
# R - need to add R repo first
echo "deb https://www.stats.bris.ac.uk/R/bin/linux/ubuntu $(lsb_release -c | xargs | cut -f2 -d' ')/" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
sudo apt-get update && sudo apt upgrade && sudo apt install libcurl4-openssl-dev libxml2-dev libcairo2-dev libxt-dev libssl-dev
sudo apt install r-base r-base-dev

# install R packages for all users
sudo R | tee -a /tmp/r.log
source("https://bioconductor.org/biocLite.R") # bioconductor
biocLite('BiocInstaller');

install.packages("GRanges");
install.packages("DataTable");
install.packages("tidyverse");
install.packages("data.table");
install.packages("flashpcaR");

```


## Running exercises

### Working in your own laptop
Copy workshop materials locally ie. `rsync -avz --exclude="*.git/" USERNAME@192.168.1.111:/ngschool/2018 ~/ngschool`,
enter NGSchoool directory `cd ~/ngschool/2018` and you are ready to work.
Make sure, you have installed [all prerequesities](#dependencies) before! 

### Working in remote NGSchool server
Login to the server with your credentials,
sync workshop materials to your home directory `rsync -av --exclude '*.git/' /ngschool/2017 ~/ngschool`, 
enter your personal NGSchoool directory `cd ~/ngschool/2017` and you are ready to work.

Make sure to import local variable in each new window
```bash
# NOTE: you may need to change `/ngschool/2018` directory
# if you cloned the repository to another location
source /ngschool/2018/.bashrc
```

### Working in VirtualBox
!!!TBD!!!
First, [get VM image](http://zdglab.iimcb.gov.pl/cluster/ngschool/2018/VM/ubuntu18.04.vdi)
and [create VM in VirtualBox using this image](http://linuxbsdos.com/2015/11/13/how-to-import-a-virtual-machine-image-into-virtualbox/). 
Then run VM (u: ngschool p: ngschool), enter NGSchoool directory `cd /ngschool/2017` and you are ready to work. 


## Cloning the repository
**This has to be done only if you wish to explore materials before the school. Otherwise, ignore below.**  
Cloning and syncing from github [before or after the school]
```bash
# get fresh copy of the repo
mkdir -p ~/ngschool && cd ~/ngschool
git clone --recursive https://github.com/NGSchoolEU/2018.git

# or sync repo to the latest version
cd ~/ngschool/2018
git pull
```

Below, we're providing links to data not included in this repository. 

### Materials not included in github repo
You can get below using `wget -nc -r -np HTTP`

Note, you can also sync all data using:
```bash
rsync -avz --exclude="*.git/" USERNAME@192.168.1.111:/ngschool/2018 ~/ngschool
# and type your password
```
