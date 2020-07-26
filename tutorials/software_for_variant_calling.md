##### Before Installation make sure you have dependencies installed, here are some command needs to run before installation if you get any error while installing these softwares
```
sudo apt-get install libbz2-dev
sudo apt install liblzma-dev
sudo apt install libcurl4-nss-dev 

```

# Bowtie2

## Installing Bowtie2

### Step one 
- Visit Bowtie2 [official website](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml) to check latest version available, we are currently using v2.4.1

#### Link to download via browser
> https://sourceforge.net/projects/bowtie-bio/files/bowtie2/

#### Link to download via terminal
```
wget https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.4.1/bowtie2-2.4.1-linux-x86_64.zip
```
### Step two
- Once you download the zip file, extract the file
```
unzip bowtie2-2.4.1-linux-x86_64.zip
```
### Step three
- Source the path of binary directory to bashrc
```
export PATH=$PATH:/path/of/your/bowtie2/directory/
```
----------------------------------------------------

# Samtools
## Installing Samtools

### Step One
- Visit the samtools [official website](http://www.htslib.org/download/) to check the latest version availabel, we are currently using v

#### Link to download via browser
> http://www.htslib.org/download/

#### Link to download via terminal
```
wget https://github.com/samtools/samtools/releases/download/1.10/samtools-1.10.tar.bz2
```

### Step Two
- Once you downloaded the file, extract it
```
tar -xf samtools-1.10.tar.bz2
```

### Step Three
- Excute the following commands to compile and install. 
- **--prefix** Be aware of that, if you want to install in current directory only, need not to give
```
cd samtools-1.10
./configure
#./configure --prefix=/where/to/install
make
make install
````
### Step Four
- Source the path of these binary to bashrc

```
export PATH=$PATH:/path/of/your/samtools/directory
```
-----------------------------------

# vcftools

## Installing vcftools

### Step One
- Visit the bcftools [official website](http://www.htslib.org/download/) to check the latest version availabel, we are currently using v

#### Link to download via browser
> http://www.htslib.org/download/

#### Link to download via terminal
```
wget https://github.com/samtools/bcftools/releases/download/1.10.2/bcftools-1.10.2.tar.bz2
```

### Step Two
- Once you downloaded the file, extract it
```
tar -xf bcftools-1.10.2.tar.bz2
```

### Step Three
- Excute the following commands to compile and install. 
- **--prefix** Be aware of that, if you want to install in current directory only, need not to give
```
cd bcftools-1.10.2
./configure
#./configure --prefix=/where/to/install
make
make install
````
### Step Four
- Source the path of these binary to bashrc

```
export PATH=$PATH:/path/of/your/bcftools/directory
```



-----------------------------------

# bcftools

## Installing bcftools

### Step One
- Visit the bcftools [official website](http://www.htslib.org/download/) to check the latest version availabel, we are currently using v

#### Link to download via browser
> http://www.htslib.org/download/

#### Link to download via terminal
```
wget https://github.com/samtools/bcftools/releases/download/1.10.2/bcftools-1.10.2.tar.bz2
```

### Step Two
- Once you downloaded the file, extract it
```
tar -xf bcftools-1.10.2.tar.bz2
```

### Step Three
- Excute the following commands to compile and install. 
- **--prefix** Be aware of that, if you want to install in current directory only, need not to give
```
cd bcftools-1.10.2
./configure
#./configure --prefix=/where/to/install
make
make install
````
### Step Four
- Source the path of these binary to bashrc

```
export PATH=$PATH:/path/of/your/bcftools/directory
```
