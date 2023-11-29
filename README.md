# Final_Project

****
The first thing that was done was accessing R Studio. R Studio is where the visual aspect of the phylogenetic tree is created

Once R Studio is open I pasted this: 

```R
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install("ggtree")

install.packages("ape") #installs package ape

library(ape) # loads package ape
library(ggtree) 
```
Once the packages were done downloading, R Studio was set aside visited again. 
Now a couple of programs to be downloaded via conda, the package manager, in order to continue. Before downloading the programs, an enviroment needed to be created.
To create a new environment you will need to type this: 

conda create --prefix Absolute/path/environment_name

The enviroment name used was "final_project"
Now that the environment has been created, I activate the environment using this command: 

'conda activate jsuarez9/final_project'

Now that I was in the intended environment, the following programs were downloaded 

conda install -c bioconda mafft
conda install -c bioconda iqtree

Since all the files needed to be in one place I made a new directory to hold everything. This was done doing this: 

 mkdir final_project  
    cd final_project
Now that the directory was created, I created a for loop to download all the genome that I would need:



for i final_project
 do
 wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/029/931/775/GCF_029931775.1_rEulEur1.hap1/GCF_029931775.1_rEulEur1.hap1_genomic.fna.gz
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/027/244/095/GCF_027244095.1_rHemCap1.1.pri/GCF_027244095.1_rHemCap1.1.pri_genomic.fna.gz
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/947/686/815/GCA_947686815.1_rPodLil1.2/GCA_947686815.1_rPodLil1.2_genomic.fna.gz
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/016/801/065/GCA_016801065.1_ASM1680106v1/GCA_016801065.1_ASM1680106v1_genomic.fna.gz
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/027/172/205/GCF_027172205.1_rPodRaf1.pri/GCF_027172205.1_rPodRaf1.pri_genomic.fna.gz
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/090/745/GCF_000090745.2_AnoCar2.0/GCF_000090745.2_AnoCar2.0_genomic.fna.gz
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/028/583/425/GCF_028583425.1_MPM_Emac_v1.0/GCF_028583425.1_MPM_Emac_v1.0_genomic.fna.gz
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/003/113/815/GCA_003113815.1_ASM311381v1/GCA_003113815.1_ASM311381v1_genomic.fna.gz
 done

Now that all the dataset was downloaded, the files needed to unzipped. The command I used was this: 

for i in final_project
do 
gzip -d GC*
echo GC*
done

Now that everything as been unzipped, it had to be unwrapped since they were not all on one line. Here is the script that I used to do that

for i in final_project
do 

awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' GCF_029931775.1_rEulEur1.hap1_genomic.fna > Tarantolino.unwrapped.fna

awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' GCF_027244095.1_rHemCap1.1.pri_genomic.fna > Graceful_crag_lizard.unwrapped.fna

awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' GCA_947686815.1_rPodLil1.2_genomic.fna > Lilfords_wall_lizard.unwrapped.fna

awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' GCA_016801065.1_ASM1680106v1_genomic.fna > Plateau_fence_lizard.unwrapped.fna

awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' GCF_027172205.1_rPodRaf1.pri_genomic.fna > Aeolian_wall_lizard.unwrapped.fna

awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' GCF_000090745.2_AnoCar2.0_genomic.fna > Green_anole.unwrapped.fna

awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' GCF_028583425.1_MPM_Emac_v1.0_genomic.fna > Leopard_gecko.unwrapped.fna

awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' GCA_003113815.1_ASM311381v1_genomic.fna > Tuatara.unwrapped.fna
done

After completing this, the sequences that the gene that I wanted need to be pulled out
