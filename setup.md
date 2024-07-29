---
title: Setup
---

# Overview

This workshop is designed to be run on pre-imaged Amazon Web Services (AWS) instances.
We will be providing you with an AWS instance.  To access your AWS instance, some additional software, detailed below, may need to be installed on your computer.


## Required additional software

- This lesson requires a working spreadsheet program.  If you have a working spreadsheet program installed on your computer, such as Microsoft Excel or [LibreOffice](https://www.libreoffice.org/) (a free, open source spreadsheet program), you can use that.  Otherwise, you can use Google Sheets.  Either option will work well for this workshop.  
- For Windows, you will also need to install either Git Bash, PuTTY, or the Ubuntu Subsystem.  Instructions are below.

:::::::::::::::: spoiler

## Windows users only:  Setting up software you can use to connect to your cloud computer

Open your Command Prompt app by searching for "cmd".  At the command prompt, type `ssh`.  Confirm that this prints out the usage information for the `ssh` command.  If the result is "Command not found" then you have a few options:

- Set up the Ubuntu Subsystem for Windows. This option is only available for Windows 10 - detailedinstructions are available at [https://docs.microsoft.com/en-us/windows/wsl/install](https://docs.microsoft.com/en-us/windows/wsl/install).
- Download the [Git for Windows installer](https://git-for-windows.github.io/).
  Run the installer and follow the steps below:
  - Click on "Next" four times (two times if you've previously installed Git).
    You don't need to change anything in the Information, location, components, and start menu screens.
  - **From the dropdown menu select "Use the Nano editor by default"
    (NOTE: you will need to scroll up to find it) and click on "Next".**
  - On the page that says "Adjusting the name of the initial branch in new repositories",
    ensure that "Let Git decide" is selected.
    This will ensure the highest level of compatibility for our lessons.
  - Ensure that "Git from the command line and also from 3rd-party software"
    is selected and click on "Next".
    (If you don't do this Git Bash will not work properly,
    requiring you to remove the Git Bash installation,
    re-run the installer and to select the
    "Git from the command line and also from 3rd-party software" option.)
  - Ensure that "Use the native Windows Secure Channel Library" is selected and click on "Next".
  - Ensure that "Checkout Windows-style, commit Unix-style line endings" is selected and click on "Next".
  - **Ensure that "Use Windows' default console window" is selected and click on "Next".**
  - Ensure that "Default (fast-forward or merge) is selected and click "Next"
  - Ensure that "Git Credential Manager Core" is selected and click on "Next".
  - Ensure that "Enable file system caching" is selected and click on "Next".
  - Click on "Install".
  - Click on "Finish".
  - Check the settings for you your "HOME" environment variable.
  - If your "HOME" environment variable is not set (or you don't know what this is):
  - Open command prompt (Open Start Menu then type `cmd` and press [Enter])
  - Type the following line into the command prompt window exactly as shown: `setx HOME "%USERPROFILE%"`
  - Press [Enter], you should see `SUCCESS: Specified value was saved.`
  - Quit command prompt by typing `exit` then pressing [Enter]
- Another option is to install the MobaXterm desktop app.  Please follow the download instructions at [mobaxterm.mobatek.net](https://mobaxterm.mobatek.net/){:target="\_blank"} to download the free edition.

:::::::::::::::::::::::::


### Data

[The data used in this workshop is available on FigShare](https://figshare.com/articles/Data_Carpentry_Genomics_beta_2_0/7726454).
Because this workshop works with real data, be aware that file sizes for the data are large.
Please read the FigShare page for information about the data and access to the data files.

More information about these data will be presented in
[the first lesson of the workshop](https://www.datacarpentry.org/organization-genomics/data/).

### Software

| Software | Version | Manual | Available for         | Description                                                           | 
| -------- | ------- | ------ | --------------------- | --------------------------------------------------------------------- |
| [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)         | 0\.11.9  | [Link](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/Help/)       | Linux, MacOS, Windows | Quality control tool for high throughput sequence data.               | 
| [Trimmomatic](https://www.usadellab.org/cms/?page=trimmomatic)         | 0\.39    | [Link](https://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/TrimmomaticManual_V0.32.pdf)       | Linux, MacOS, Windows | A flexible read trimming tool for Illumina NGS data.                  | 
| [BWA](https://bio-bwa.sourceforge.net/)         | 0\.7.17  | [Link](https://bio-bwa.sourceforge.net/bwa.shtml)       | Linux, MacOS          | Mapping DNA sequences against reference genome.                       | 
| [SAMtools](https://samtools.sourceforge.net/)         | 1\.9     | [Link](https://www.htslib.org/doc/samtools.html)       | Linux, MacOS          | Utilities for manipulating alignments in the SAM format.              | 
| [BCFtools](https://samtools.github.io/bcftools/)         | 1\.9     | [Link](https://samtools.github.io/bcftools/bcftools.html)       | Linux, MacOS          | Utilities for variant calling and manipulating VCFs and BCFs.         | 
| [IGV](https://software.broadinstitute.org/software/igv/home)         | [Link](https://software.broadinstitute.org/software/igv/download)        | [Link](https://software.broadinstitute.org/software/igv/UserGuide)       | Linux, MacOS, Windows | Visualization and interactive exploration of large genomics datasets. | 

### QuickStart Software Installation Instructions

These are the QuickStart installation instructions.
They assume familiarity with the command line and with installation in general.
As there are different operating systems and many different versions of
operating systems and environments, these may not work on your computer.
If an installation doesn't work for you, please refer to the user guide for the tool,
listed in the table above.

We have installed software using [Conda](https://conda.io).
Conda is a package manager that simplifies the installation process.
Please first install Conda through the Miniconda installer (see below) before proceeding to the installation of individual tools.
For more information on Miniconda, please refer to the Conda [documentation](https://conda.io/projects/conda/en/latest/user-guide/install/index.html).

### Conda

:::::::::::::::: spoiler

## Linux

To install Conda, type:

```bash
$ curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
$ bash Miniconda3-latest-Linux-x86_64.sh
```

Then, follow the instructions that you are prompted with on the screen to install Conda.

:::::::::::::::::::::::::

:::::::::::::::: spoiler

## MacOS

To install Conda, type:

```bash
$ curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
$ bash Miniconda3-latest-MacOSX-x86_64.sh
```

Then, follow the instructions that you are prompted with on the screen to install Conda.

:::::::::::::::::::::::::

### FastQC

:::::::::::::::: spoiler

## MacOS

To install FastQC, type:

```bash
$ conda install -c bioconda fastqc=0.11.9
```

:::::::::::::::::::::::::

:::::::::::::::: spoiler

## FastQC Source Code Installation

If you prefer to install from source, follow the directions below:

```bash
$ cd ~/src
$ curl -O http://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.11.9.zip
$ unzip fastqc_v0.11.9.zip
```

Link the fastqc executable to the ~/bin folder that
you have already added to the path.

```bash
$ ln -sf ~/src/FastQC/fastqc ~/bin/fastqc
```

Due to what seems a packaging error
the executable flag on the fastqc program is not set.
We need to set it ourselves.

```bash
$ chmod +x ~/bin/fastqc
```

:::::::::::::::::::::::::

**Test your installation by running:**

```bash
$ fastqc -h
```

### Trimmomatic

:::::::::::::::: spoiler

## MacOS

```bash
conda install -c bioconda trimmomatic=0.39
```

:::::::::::::::::::::::::

:::::::::::::::: spoiler

## Trimmomatic Source Code Installation

If you prefer to install from source, follow the directions below:

```bash
$ cd ~/src
$ curl -O http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.39.zip
$ unzip Trimmomatic-0.39.zip
```

The program can be invoked via:

```
$ java -jar ~/src/Trimmomatic-0.39/trimmomatic-0.39.jar
```

The ~/src/Trimmomatic-0.39/adapters/ directory contains
Illumina specific adapter sequences.

```bash
$ ls ~/src/Trimmomatic-0.39/adapters/
```

:::::::::::::::::::::::::

**Test your installation by running:** (assuming things are installed in ~/src)

```bash
$ java -jar ~/src/Trimmomatic-0.39/trimmomatic-0.39.jar
```

:::::::::::::::: spoiler

## Simplify the Invocation, or to Test your installation if you installed with miniconda3:

To simplify the invocation you could also create a script in the ~/bin folder:

```bash
$ echo '#!/bin/bash' > ~/bin/trimmomatic
$ echo 'java -jar ~/src/Trimmomatic-0.39/trimmomatic-0.39.jar $@' >> ~/bin/trimmomatic
$ chmod +x ~/bin/trimmomatic
```

Test your script by running:

```bash
$ trimmomatic
```

:::::::::::::::::::::::::

### BWA

:::::::::::::::: spoiler

## MacOS

```bash
conda install -c bioconda bwa=0.7.17=ha92aebf_3
```

:::::::::::::::::::::::::

:::::::::::::::: spoiler

## BWA Source Code Installation

If you prefer to install from source, follow the instructions below:

```bash
$ cd ~/src
$ curl -OL http://sourceforge.net/projects/bio-bwa/files/bwa-0.7.17.tar.bz2
$ tar jxvf bwa-0.7.17.tar.bz2
$ cd bwa-0.7.17
$ make
$ export PATH=~/src/bwa-0.7.17:$PATH
```

:::::::::::::::::::::::::

**Test your installation by running:**

```bash
$ bwa
```

### SAMtools

:::::::::::::::: spoiler

## MacOS

```bash
$ conda install -c bioconda samtools=1.9=h8ee4bcc_1
```

:::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## SAMtools Versions

SAMtools has changed the command line invocation (for the better).
But this means that most of the tutorials on the web indicate an older and obsolete usage.

Using SAMtools version 1.9 is important to work with the commands we present in these lessons.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::: spoiler

## SAMtools Source Code Installation

If you prefer to install from source, follow the instructions below:

```bash
$ cd ~/src
$ curl -OkL https://github.com/samtools/samtools/releases/download/1.9/samtools-1.9.tar.bz2
$ tar jxvf samtools-1.9.tar.bz2
$ cd samtools-1.9
$ make
```

Add directory to the path if necessary:

```bash
$ echo export `PATH=~/src/samtools-1.9:$PATH` >> ~/.bashrc
$ source ~/.bashrc
```

:::::::::::::::::::::::::

**Test your installation by running:**

```bash
$ samtools
```

### BCFtools

:::::::::::::::: spoiler

## MacOS

```bash
$ conda install -c bioconda bcftools=1.9
```

:::::::::::::::::::::::::

:::::::::::::::: spoiler

## BCF tools Source Code Installation

If you prefer to install from source, follow the instructions below:

```bash
$ cd ~/src
$ curl -OkL https://github.com/samtools/bcftools/releases/download/1.9/bcftools-1.9.tar.bz2
$ tar jxvf bcftools-1.9.tar.bz2
$ cd bcftools-1.9
$ make
```

Add directory to the path if necessary:

```bash
$ echo export `PATH=~/src/bcftools-1.9:$PATH` >> ~/.bashrc
$ source ~/.bashrc
```

:::::::::::::::::::::::::

**Test your installation by running:**

```bash
$ bcftools
```

### IGV

- [Download the IGV installation files](https://software.broadinstitute.org/software/igv/download)
- [Install and run IGV using the instructions for your operating system](https://software.broadinstitute.org/software/igv/download).


