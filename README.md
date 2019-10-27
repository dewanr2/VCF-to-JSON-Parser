# Find-Variant-VCF-to-JSON
Goal : 

We will parse a variant call format file. This file has one thousand variants in it. Each line after the header lines is a variant. We'll open the variant file and inspect its contents. We will parse each line and transform it into a JSON. The output will look something like this (I have shortened the output):

{
        "ALT": "G",
        "CHROM": "4",
        "FILTER": "PASS",
        "ID": ".",
        "INFO": {

            "Gene.ensGene": "ENSG00000109471,ENSG00000138684",
            "Gene.refGene": "IL2,IL21",
            "GeneDetail.ensGene": "dist=38306,dist=117597",
            "GeneDetail.refGene": "dist=38536,dist=117597"
        },
        "POS": 123416186,
        "QUAL" :23.25,
        "REF": "A",
        "SAMPLE": {
            "XG102": {
                "AD": "51,8",
                "DP": "59",
                "GQ": "32",
                "GT": "0/1",
                "PL": "32,0,1388"
            }
    }
This project has several small functions that will be used to generate the JSON above. Note that the method outlined is not necessarily optimal. It is just one way of parsing the file after breaking a large problem into small parts.

Note that the header which corresponds to the columns starts with one hash/pound (#) symbol. Skip all headers that start with two hashes/pounds (##).
