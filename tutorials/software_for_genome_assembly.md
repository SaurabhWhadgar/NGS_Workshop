# Genome Assembly using velvet 


## While installing the velvet we might expect some error. Here are some expected error and their solution

- Make not found
- Obj.h ( header files not found)
- Zlib.h not found
- Unzip not found

Way to resolve these errors

```
sudo apt install gcc
sudo apt-get install libz-dev
sudo apt-get install zlib1g-dev
sudo apt-get install unzip
```

## Installing Velvet

1) Downloading velevet software
```
wget https://www.ebi.ac.uk/~zerbino/velvet/velvet_1.2.10.tgz 
```
2) Extracting velvet files
```
tar -zxvf velvet_1.2.10.tgz
```
- Make Sure that if you are going to user Kmer lengh more than 31 (which default kmer lenght for velvet) you need to do make with MAX KMER lenght that you are going to use

3) make step
```
cd velvet_1.2.10
make # ( For using 31 default kmer length) OR
make MAXKMERLENGTH=100 # ( Which tells that will be using kmers of size less than 100 )
```

## Once you successfully complied and installed velvet, we are ready to make these software globally available using exporting the paths in bashrc
- In terminal type
```
pwd
```
once you got the present working directory path (pwd) copy this path, we need to paste this path in bashrc

```
gedit ~/.bashrc
# Or you can open bashrc in any text editor like vi, vim, sublime, code
```
## Exporting path

```
# export PATH=$PATH:*Paste your pwd path here*
# This will be first and formost important part of command which will be common in all path we are going to export
# For example

export PATH=$PATH:/home/saurabh/software/velvet_1.2.10

# It means that export path (pwd) in which my velvet is installed. so it will give direct access to all the excutable files present in the velvet_1.2.10 directory
# If your excutable are present in ( /home/username/software/anysoftware/bin/excutable files) then your export path will become 
# export PATH=$PATH:/home/username/software/anysoftware/bin
```
Save the files and then do
## Sourcing bashrc

```
source ~/.bashrc
```
Now you can access velveth, velvetg excutable in any terminal 
