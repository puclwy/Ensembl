## Use Ensembl REST API Endpoints (https://rest.ensembl.org/) to retreive paired-wise cross-species genomic location alignement. 
`GET alignment/region/:species/:region` to retrieve genomic alignments as separate blocks based on a region and species
```
import requests, sys
 
server = "https://rest.ensembl.org"
ext = "/alignment/region/taeniopygia_guttata/3:106040329-106040379?method=LASTZ_NET;species_set=taeniopygia_guttata;species_set=gallus_gallus"
 
r = requests.get(server+ext, headers={ "Content-Type" : "application/json"})
 
if not r.ok:
  r.raise_for_status()
  sys.exit()
 
decoded = r.json()
print(repr(decoded))
```
- **Input file:** Lists of splice sites of interest. Columns include: gene, chr, strand, motif_seq, motif_start, motif_end 
- **Downstream analyses:** 1) Cross-species motif analyses and comparison. 2) RNA-seq integration to understand splice site utlization under perturbation cross conditions and species. 
