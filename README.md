# fivepseqenhancer
fivepseqenhancer builds upon the capabilities of the original Fivepseq package by introducing enhanced functionality. It categorizes genes in the input genome, enabling users to characterize the diverse responses of different gene types to antibiotic treatments. Additionally, fivepseqenhancer provides a clear visualization of antibiotic response at the codon level, pinpointing the antibiotic target sites with precision.
## Requirements and Installation
It is recommended to create a dedicated Conda environment to install the dependencies required for fivepseqenhancer.
```bash
conda create -n fivepseqenhancer python=3 r-base=3.6.3
conda activate fivepseqenhancer
```
### Dependencies
```bash
git clone https://github.com/joshuagryphon/plastid -b develop
cd plastid
python setup.py install
pip install --upgrade numpy==1.19.5 pysam==0.19.0 cython==0.29.28
```
### Fivepseq installation
```bash
git clone https://github.com/lilit-nersisyan/fivepseq.git
python setup.py install
```
### Fivepseqenhancer installation
```bash
git clone https://github.com/whchenlab/5pseqenhancer.git
```
Configuring Environment Variables
```bash
export PATH={your_fivepseqenhancer_path}/src:$PATH
```
## Data preparation
Aligned reads (.bam)  
Alignment index (.bai)  
Genomic sequence file (.fasta / .fa)  
Genomic annotation file (.gff/ .gtf)  
COG database csv file (.csv)  
COG database tab file (.tab)
### Aligned reads (.bam)
Users’ raw `.fastq` data must undergo quality control, adapter trimming, UMI extraction (if applicable), alignment to the reference genome, and UMI deduplication to produce the final `.bam` file for input. Specific operations on the `.fastq` files can be referenced at [preparing data](https://fivepseq.readthedocs.io/en/latest/preparing_data.html "preparing data").
### COG database files (.csv & .tab)
Users need to download the `cog-20.cog.csv` file and the `cog-20.def.tab` file from the COG database website [COG database](https://ftp.ncbi.nlm.nih.gov/pub/COG/COG2020/data/ "COG database").
## Usage
```bash
fivepseqenhancer \
  --ref_fasta {fasta} \
  --ref_gff {gff} \
  --cog_csv cog-20.cog.csv \
  --cog_tab cog-20.def.tab \
  --output {output dir}
  --bams {bam dir}
```
Complete options
You can run fivepseqenhancer --help to see all options.
```bash
usage: fivepseqenhancer [OPTIONS]

option:
  --ref_fasta    Reference genome fasta file
  --ref_gff      Reference genome gene annotation file (.gff/.gff3)
  --cog_csv      COG database files (.csv)
  --cog_tab      COG database files (.tab)
  --output       Output directory
  --bams
  --help         Display help information
```
