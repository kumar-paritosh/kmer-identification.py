# kmer-identification.py
This script can be used to find kmers and its count in the given region
USAGE:
python kmer-idntification.py -d DNA_SEQ -k KMER_LENG -m MIN_COUNT -s START -e END

Where:
 DNA_SEQ = single sequence file in fasta format
 KMER_LENG = minimum kmer size for the repeat (preferably >100bp)
 MIN_COUNT = minimum count of the kmers for qualifying the specific category
 START = Starting base of the putative centromeric region
 END = Last base of the putative centromeric region
 
