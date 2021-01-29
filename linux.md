# Download SARS-COV-2 whole genome sequence (Format: fastq Layout: paired)

	fastq-dump -I --split-files SRR11479042
	
	bwa index -p covid sarscov2_refgenome.fasta
	
	bwa mem -M -t 8 covid SRR13491098_1.fastq SRR13491098_2.fastq > covid.sam
	
	samtools fixmate -O bam covid.sam covid.bam
	
	samtools sort -T temp.prefix -0 bam -@ 8 -o covid.sorted.bam covid.bam 
