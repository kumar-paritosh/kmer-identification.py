import argparse
import os
import sys
import re


# Argument parsing

ap = argparse.ArgumentParser(description='Kmer based centromere specific repeat identification.')

ap.add_argument("-d", "--dna_seq", required=True, help="Single DNA sequence in fasta format")
ap.add_argument("-k", "--kmer_leng", required=True, help="minimum kmer size")
ap.add_argument("-m", "--min_count", required=True, help="minimum count of the kmer")
ap.add_argument("-s", "--start", required=True, help="Start of the centromeric region")
ap.add_argument("-e", "--end", required=True, help="End of the centromeric region")

args = vars(ap.parse_args())

print("Your entered source is %s and destination folder is %s", args['kmer_leng'], args['min_count'])


# define the function to split dna
def split_dna(dna, kmer_size):
    kmers = []
    for start in range(0,len(dna)-(kmer_size -1),1):
        kmer = dna[start:start+kmer_size]
        kmers.append(kmer)
    return kmers

def read_FASTA(filename):
    with open(filename) as file:
            contents = file.read()
            entries = contents.split('>')[1:]
            partitioned_entries = [entry.partition('\n') for entry in entries]
            pairs = [(pair[0].split('|'), pair[2].replace('\n', '')) for pair in partitioned_entries]
            return pairs
            #for pairs in pairs:
            	

kmer_counts = {}
# process each file with the right name
dna_file = read_FASTA(arg['dna_seq'])
#dna = str(dna_file[1])
#print(dna_file)
#dna = str(dna_file[1])
# process each DNA sequence in a file
for line in dna_file:
    dna = str(line[1]).upper()[start:end]
    #print(dna)
    # increase the count for each k-mer that we find
    for kmer in split_dna(dna, arg['kmer_leng']):
        current_count = kmer_counts.get(kmer, 0)
        new_count = current_count + 1
        kmer_counts[kmer] = new_count
# print k-mers whose counts are above the cutoff
for kmer, count in kmer_counts.items():
    if count > count_cutoff:
        print(kmer + " : " + str(count))
