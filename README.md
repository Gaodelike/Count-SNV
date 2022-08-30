# Count-SNV
# bam2vaf
该脚本为统计扩增子测序的snp和indel突变频率的脚本，输入文件为sort后的bam文件(需要索引)和对应位置的bed文件

# Usage
`python3 bam2vaf.py -bam $bam -bed $bed -fa $fa -od $PWD -n "rawbam"`

```
usage: Detect snv and indel
       [-h] [-bam BAM] [-bed BED] [-d DEPTH] [-n NAME] [-mq MAPQ] [-bq BASEQ]
       [-fa FASTA] [-od OUTDIR]

optional arguments:
  -h, --help  show this help message and exit
  -bam BAM    bam file
  -bed BED    bed file
  -d DEPTH    max depth
  -n NAME     samplel name
  -mq MAPQ    map quality
  -bq BASEQ   base quality
  -fa FASTA   reference fasta file
  -od OUTDIR  output dir
```
`-bam`: input bam file

`-bed`: BED file

`-fa` : reference fasta file

`-d`  : max depth limit, same as samtools mpileup. [default: 100000]

`-n`  : sample name

`-mq` : mapping quailty cutoff. [default: 0]

`-bq` : base quality. [default: 0]

`-od` : output dir

```
python3 ../bam2vaf.py -bam $line -bed $bed -fa $fa -od $PWD -n $name
```


# Outfiles
The outfile is `<sample_name>.variants.xls`

## Outfile Format
```
Chr     Pos             Ref         Alt          AltNum      Depth      AltAlleleFrequency
chr12   52380364        T           ref-homo     0           24         0.0     
chr12   52380365        T           C            1           24         0.042
chr12   52380366        A           ref-homo     0           24         0.0
chr12   52380623        TGATGA      T            90          582        0.155
chrX    48649699        C           CTACT        30          155        0.194
```


# Dependency
* Python3
* Pysam 0.16.0.1
