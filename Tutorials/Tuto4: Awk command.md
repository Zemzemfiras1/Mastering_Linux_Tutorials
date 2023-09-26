##  Pracatical for Awk command

 * By the end of this tutorial you will be able to : 
   - Improve text processing skills.
   - Extract & Transform your data.
   - Clean & validate your data.
---------------------------------------------------------------------------------------------------------------------------------
#### +++ Introduction : Command's examples : 
---------------------------------------------------------------------------------------------------------------------------------
1. Download the gff file exmaple from this link above in your working directory Dir3. 
   - Check your path, use pwd command.
   - Hint : use wget command to download the file.
   - link : 

2. To print the content of your file please type this command;

```markdown
 cat GFFgile 
```

3. Print out the content of the GFFfile by "Aho, Weinberger, and Kernighan" command;

```markdown
awk '{print}' GFFfile 
```

4. Repeat question 3 and substitute "print" by "print $0", is there any difference ? 

```markdown
awk '{print $0}' GFFfile 
```

5. In case you wanted to print a ormatted output, you may type; 

```markdown
awk '{printf $0}' GFFfile 
```

6. How many lines contain the GFFfile. ( use wc command with the option -l ); 

```markdown
 cat GFFgile | wc -l 
```

7. To print the current line number using awk just type;

```markdown
awk '{print NR}' GFFfile  
```

* If you are confused and you wanted to check again, you could pipe the previous command's output to wc -l command. 

8. Note that awk is a programming language, so you can use implement many options using a single command, First lets print how many field contains each line; 

```markdown
awk '{print NF}' GFFfile 
```

9. Now Try to append NF and NR in one command ;


<details>
<summary> Hint </summary>
<p> You could write a string in your command exp awk '{ ... ,"your string", ...}' input </p> 
</details>
<details>
<summary> Answer: </summary>

```markdown
 awk '{print "The number of field in line",NR," is : ", NF}' GFFfile 
```
</details>

10. Supposing that You wanted to print out specific fields, awk offer you this ability, try to print field number 1,3,4,5,7,9 then redirect the output to a  modified newfile named mGFFfile;

```markdown
awk  '{print $1,$3,$4,$5,$7,$9}' GFFfile > mGFFfile
```

11. Inspect your new file use " more " command.
  - See that mFFfile bacame non a tab separated file so to get your output in "\t" format, change awk’s default behaviour by using the "Output Field Separator(OFS)" 

```markdown
awk  'BEGIN {OFS="\t"} {print $1,$3,$4,$5,$7,$9}' GFFfile > mGFFfile
```

  - Inspect again your new file. 





















