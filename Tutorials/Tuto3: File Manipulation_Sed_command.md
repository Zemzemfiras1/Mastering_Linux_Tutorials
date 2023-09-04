##  

 * For this tutorial we will manupilate file by sed commands.

 * Sed is one of the most used rapid and powerfull unix commands. It stands for "stram eaditor". while it is like grep command, can fetch into files and search for spécified patterns "matching", it can also perform substitution, insertion and deletion functions. Its syntax : 

sed OPTIONS.. [scripts] [Inputfile]

#### +++ Introduction : Command's examples : 

```markdown
sed 's/sad/happy/' myInputfile.txt
```

 * The “ s ” specifies the substitution operation, “ / ” are delimiters, the “sad” is the search pattern and the “happy” is the replacement string.

```markdown
sed '/Thomas/d' Path_to_success.txt 
```

 * The “ d ” specifies the deletion operation Deletes, and it deletes lines which contains the matched pattern from the input file.

```markdown 
sed -n '1,3p' Path_to_success.txt 
```
  
 * This command print out the firt 3 lines, the print operation is specified by “ d ” and the “ -n ” is for suppressing automatic printing of pattern space.

**Note** that we can combine commands by “ -e ” using option. 

```markdown
sed -e 's/sad/happy/' -e'/Thomas/d' Path_to_success.txt 
```



