# Cheat-Sheet

**Use Awk to find the max value in a column**
```
awk -v max=0 'FNR > 1 {if($1>max){want=$0; max=$1}}END{print want} ' file
```
Where it will fined the highest value in column 1, skipping the header. 
