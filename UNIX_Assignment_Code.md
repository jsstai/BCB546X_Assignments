#UNIX Assignment


##Data Inspection


###Attributes of `fang_et_al_genotypes `

Here is my snippet of code used for data inspection


    (head -n 3; tail -n 3) < fang_et_al_genotypes.txt

    awk -F "\t" '{print NF; exit}' fang_et_al_genotypes.txt

    du -h fang_et_al_genotypes.txt

    wc fang_et_al_genotypes.txt

    file fang_et_al_genotypes.txt


By inspecting this file I learned that:

- The number of columns in the `fang_et_al_genotypes` is **986**.
- The file size is **6.1 M**.
- The number of lines is **2783** and the number of words is **2744038**.
- The file is an **ASCII text file** with very long lines



###Attributes of `snp_position.txt`

Here is my snippet of code used for data inspection

	(head -n 3; tail -n 3) < snp_position.txt

    awk -F "\t" '{print NF; exit}' snp_position.txt

    du -h snp_position.txt

    wc snp_position.txt

    file snp_position.txt

By inspecting this file I learned that:

- The number of columns in the `snp_position.txt` file is **15**.
- The file size is **38K**.
- The number of lines in the file is **984** and the number of words is **13198**.
- The file is an **ASCII text file**.


##Data Processing


Here is my snippet of code used for data processing of snp_position.txt

    cut -f 1,3,4 snp_position.txt > extracted_snp_position.txt

    (head -n 1 extracted_snp_position.txt && tail -n +2 extracted_snp_position.txt |sort -k1,1) > sorted_extracted_snp_position.txt

    tail -n+2 sorted_extracted_snp_position.txt | sort -c -k1,1

    head sorted_extracted_snp_position | column -t

Here is my brief description of what this code does:
 
- The first line of the code will **cut** columns SNP_ID, Chromosome and Position and the standard out directed to extracted_snp_position.txt. 
- The second line of code uses the **sort** command to sort the contents of the file with the header line not included in the sorting process. 
- The third and the fourth line is a diagnostic code to check whether the file has been sorted correctly.  



###Maize Data


Here is my snippet of code used for Maize data


    sort -k3 fang_et_genotypes.ext | cut -f 3| uniq -c | column -t 

    awk -F "\t" '$3 ~ /Group|ZMMIL|ZMMLR|ZMMMR/' fang_et_al_genotypes.txt | cut -f 1,4-986  > maize_genotypes.txt

    awk -f transpose.awk maize_genotypes.txt > transposed_maize_genotypes.txttransposed_maize_genotypes.txt

    (head -n 1 transposed_maize_genotypes.txt && tail -n +2 transposed_maize_genotypes.txt |sort -k1,1) > sorted_transposed_maize_genotypes.txt

    join -1 1 -2 1 --header sorted_extracted_snp_position.txt -t $'\t' sorted_transposed_maize_genotypes_.txt > merged_maize_genotypes.txt

    awk -F "\t" '{print NF;exit}' merged_maize_genotypes.txt


    (head -n 1 merged_maize_known.txt && awk '$2 == 1' merged_maize_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr1_ascend_maize.txt`
    (head -n 1 merged_maize_known.txt && awk '$2 == 2' merged_maize_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr2_ascend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 3' merged_maize_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr3_ascend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 4' merged_maize_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr4_ascend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 5' merged_maize_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr5_ascend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 6' merged_maize_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr6_ascend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 7' merged_maize_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr7_ascend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 8' merged_maize_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr8_ascend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 9' merged_maize_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr9_ascend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 10' merged_maize_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr10_ascend_maize.txt

    (head -n 1 merged_maize_known.txt && awk '$2 == 1' merged_maize_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr1_descend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 2' merged_maize_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr2_descend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 3' merged_maize_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr3_descend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 4' merged_maize_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr4_descend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 5' merged_maize_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr5_descend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 7' merged_maize_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr7_descend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 8' merged_maize_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr8_descend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 9' merged_maize_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr9_descend_maize.txt
    (head -n 1 merged_maize_known.txt && awk '$2 == 10' merged_maize_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr10_descend_maize.txt

    (head -n 1 merged_maize_genotypes.txt && awk '$3 ~ /unknown/' merged_maize_genotypes.txt) > maize_unknown_position.txt
    (head -n 1 merged_maize_genotypes.txt && awk '$3 ~ /multiple/' merged_maize_genotypes.txt)> maize__multiple_position.txt 
    

Here is my brief description of what this code does.

- The **sort** command enlists the types and number of groups present in file. 
- The **awk** command extracts the Maize groups ZMMIL,ZMMIL,ZMMMR and the header 'Group' to the `maize_genotypes.txt` file
- The awk -f transpose.awk transposes the file to convert the rows into columns to get the `transposed_maize_genotypes.txt`file.
- Next the file is sorted before joining to get the `sorted_transposed_maize_genotypes.txt `
- The **join** command will help join the `sorted_transposed_maize_genotypes.txt` file to the `sorted_extracted_snp_position.txt` without including the header. 
- The next line of code using **awk** crops out rows with multiple and unknown positions from the merged file to keep the numeric positions to get `merged_maize_known.txt`
- This file is then used with the **sort** and **sed** commands to get 10 files with ascending positions with missing data denoted by '?' and 10 files with descending positions with missing data denoted by '-'
- The last couple of codes use **awk** and help to extract the files to get `maize_unknown_position.txt` and `maize_multiple_position.txt` files


###Teosinte Data

Here is my snippet of code used for Teosinte data

    

    awk -F "\t" '$3 ~ /Group|ZM|ZMMLR|ZMMMR/' fang_et_al_genotypes.txt | cut -f 1,4-986  > teosinte_genotypes.txt

    awk -f transpose.awk teosinte_genotypes.txt > transposed_teosinte_genotypes.txt

    (head -n 1 transposed_teosinte_genotypes.txt && tail -n +2 transposed_teosinte_genotypes.txt |sort -k1,1) >sorted_transposed_teosinte_genotypes.txt

    join -1 1 -2 1 --header sorted_extracted_snp_position.txt -t $'\t' sorted_transposed_teosinte_genotypes.txt > merged_teosinte_genotypes.txt

    awk -F "\t" '{print NF;exit}' merged_teosinte_genotypes.txt

   	`(head -n 1 merged_teosinte_known.txt && awk '$2 == 1' merged_teosinte_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr1_ascend_teosinte.txt`
    (head -n 1 merged_teosinte_known.txt && awk '$2 == 2' merged_teosinte_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr2_ascend_teosinte.txt
    (head -n 1 merged_teosinte_known.txt && awk '$2 == 3' merged_teosinte_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr3_ascend_teosinte.txt
    (head -n 1 merged_teosinte_known.txt && awk '$2 == 4' merged_teosinte_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr4_ascend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 5' merged_teosinte_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr5_ascend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 6' merged_teosinte_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr6_ascend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 7' merged_teosinte_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr7_ascend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 8' merged_teosinte_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr8_ascend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 9' merged_teosinte_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr9_ascend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 10' merged_teosinte_known.txt | sort -k 3n | sed 's/?\/?/?/g') > chr10_ascend_teosinte.txt

     (head -n 1 merged_maize_known.txt && awk '$2 == 9' merged_maize_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr9_descend_maize.txt
     (head -n 1 merged_maize_known.txt && awk '$2 == 1' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr1_descend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 1' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr1_descend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 2' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr2_descend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 3' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr3_descend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 4' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr4_descend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 5' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr5_descend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 6' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr6_descend_teosinte.txt
    (head -n 1 merged_teosinte_known.txt && awk '$2 == 7' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr7_descend_teosinte.txt
     (head -n 1 merged_teosinte_known.txt && awk '$2 == 8' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr8_descend_teosinte.txt
    (head -n 1 merged_teosinte_known.txt && awk '$2 == 9' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr9_descend_teosinte.txt
    (head -n 1 merged_teosinte_known.txt && awk '$2 == 10' merged_teosinte_known.txt | sort -k 3nr | sed 's/?\/?/-/g') > chr10_descend_teosinte.txt
    

    (head -n 1 merged_teosinte_genotypes.txt awk '$3 ~ /unknown/' merged_teosinte_genotypes.txt) > teosinte_unknown_position.txt
    (head -n 1 merged_teosinte_genotypes.txt && awk '$3 ~ /multiple/' merged_teosinte_genotypes.txt) > teosinte_multiple_position.txt


  
Here is my brief description of what this code does
 
- The **awk** command extracts the Teosinte groups ZMPBA, ZMPIL, and ZMPJA and the header 'Group' to the `teosinte_genotypes.txt` file
- The awk -f transpose.awk transposes the file to convert the rows into columns to get the `transposed_teosinte_genotypes.txt`file.
- Next the file is sorted before joining to get the `sorted_transposed_teosinte_genotypes.txt `
- The **join** command will help join the `sorted_transposed_teosinte_genotypes.txt` file to the `sorted_extracted_snp_position.txt` without including the header. 
- The next line of code using **awk** crops out rows with multiple and unknown positions from the merged file to keep the numeric positions to get `merged_teosinte_known.txt`
- This file is then used with the **sort** and **sed** commands to get 10 files with ascending positions with missing data denoted by '?' and 10 files with descending positions with missing data denoted by '-'
- The last couple of codes use **awk** and help to extract the files to get `teosinte_unknown_position.txt` and `teosinte_multiple_position.txt` files