##  Pracatical for Awk command

 * By the end of this tutorial you will be able to : 
   - Improve text processing skills.
   - Extract & Transform your data.
   - Clean & validate your data.
---------------------------------------------------------------------------------------------------------------------------------
#### +++ Print-Command examples : 
---------------------------------------------------------------------------------------------------------------------------------
1. Download the gff file exmaple from this link above in your working directory Dir3. 
   - Check your path, use pwd command.
   - Hint : use wget command to download the file.
   - link : https://github.com/Zemzemfiras1/Mastering_Linux_Tutorials/blob/master/Tutorials/GFFfile
    :: [source](https://github.com/The-Sequence-Ontology/Specifications/blob/master/gff3.md)
2. To print the content of your file please type this command;

```markdown
 cat GFFgile 
```

3. Print out the content of the GFFfile by "Aho, Weinberger, and Kernighan" command;

```markdown
awk '{print}' GFFfile 
```

4. Repeat question 3 and substitute "{print}" by " '//' ", is there any difference ? 

```markdown
awk '//' mGFFfile 
```

5. Repeat question 3 and substitute "print" by "print $0", is there any difference ? 

```markdown
awk '{print $0}' GFFfile 
```

6. In case you wanted to print a ormatted output, you may type; 

```markdown
awk '{printf $0}' GFFfile 
```

7. How many lines contain the GFFfile. ( use wc command with the option -l ); 

```markdown
 cat GFFgile | wc -l 
```

8. To print the current line number using awk just type;

```markdown
awk '{print NR}' GFFfile  
```

* If you are confused and you wanted to check again, you could pipe the previous command's output to wc -l command. 

9. Note that awk is a programming language, so you can use implement many options using a single command, First lets print how many field contains each line; 

```markdown
awk '{print NF}' GFFfile 
```

10. Now Try to append NF and NR in one command ;


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
---------------------------------------------------------------------------------------------------------------------------------
#### +++ Filter lines based on conditions: 
---------------------------------------------------------------------------------------------------------------------------------
* In this part of the TUTO we will work only on mGFFfile. 

12. Extract only lines which contain CDS; 

```markdown
 awk '/CDS/' mGFFfile 
```

* To be more acurate you can specify the field(column); 

```markdown
awk '$2=="CDS" {print}' mGFFfile 
```

13. Extract lines which contain CDS or data with End position greater 5000 ( column 4 ) ; 
  - for more information about gff files : please visit ; http://www.ensembl.org/info/website/upload/gff3.html

```markdown
awk '$2=="CDS" || $3>5000 {print}' mGFFfile
```

14. Repeat question 13 then print out both lines with CDS which contain end position > 5000; 

```markdown
awk '$2=="CDS" && $3>5000 {print}' mGFFfile 
```

15. Print only unique type of feature ( $2 ); 

```markdown
awk -F'\t' '{print $2}' mGFFfile | uniq
```

16. Assuming that you wanted to print lines longer than a certain length (exp : print out words longer than 4 in the second field);

```markdown
 awk 'length($2) > 4' mGFFfile 
```

17. Repeat Q16, try to select only words with length equal to 4; 
<details>
<summary> Answer: </summary>

```markdown
awk 'length($2)== 4' mGFFfile 
```

</details>

18. Try Print a specific line (Hint: Use NR to print the 10th line);

```markdown
awk 'NR==10' mGFFfile
```

20. Calculate and print the average of values in the third column; 

```markdown
awk '{sum += $3} END {print "Average:", sum/NR}' mGFFfile 
```

21. Calculate the diference between column 4 and 3 ; 

```markdown
awk '{diff = $4 - $3; print diff}' mGFFfile
```

22. Perform the command in Q21 to calculate the sum of the differences between column 4 and column 3 for all lines in the file and print the result at the end, you can modify the Awk command as follows; 

```markdwon
 awk ' {diff = $4 - $3; sum += diff} END {print "Sum of difference: ", sum}' mGFFfile 
```

- You may also define initial variables as bellow ( add BEGIN{variable1;variable2;...;VariableN}; 

```markdwon
awk 'BEGIN{sum=0;diff=0} {diff = $4 - $3; sum += diff} END {print "Sum:", sum}' mGFFfile 
```
23. Furthemore, Awk command offer you the ability to change and append specific field or patterns, so Let us; 
  * change the non-existing field 7 from "." to "human" and append the substitution to lines which do not have this field :  

```markdown 
awk '{$7 = "Human"} 1' mGFFfile 
```

 * Only change existing field; 

```markdown 
awk '{$2 = "HumaN"} 1' GFFfile
```

 * Substitute "." by  "Human" in column 11) in GFFfile; 

```markdown 
awk '{gsub(".", "Human", $11)} 1 ' GFFfile 
```

<details>
<summary> Note : </summary>
<p>
   => Note1 : that gsub is a built-in function in Awk that stands for "global substitution." It is used to search for a pattern within each line of input text and replace all occurrences of that pattern with a specified replacement text: 
       * "." : Is the :regexp: regular expression pattern you want to search for within the target string.
       * "Human" : IS the :replacement: the text that you want to replace the matched pattern with.
       * $1 : IS the :target: the variable or field where you want to perform the substitution. 
       * 1 :IS a common Awk idiom that means to print the modified line.
   
   => Note2 : Nothing here to be changer as the reason there is no field 11 to change. 
</p>
</details>

 * Repeat the previous step with a target field equal to 2 ; what do you notice ? 

```markdown 
awk '{gsub(".", "Human", $2)} 1 ' GFFfile 
```

 * Try to substitute "CDS" with "test" only in the second field in GFFfile; Do not forget to use OFS. 

<details>
<summary> Answer : </summary>

```markdown 
awk 'BEGIN{OFS="\t"} {gsub("CDS", "test", $2)} 1' mGFFfile 
```

</details>

###### Congratulations! You've covered almost the fundamentals basics  of Awk commands. Get ready for more advanced topics in the upcoming tutorials.

