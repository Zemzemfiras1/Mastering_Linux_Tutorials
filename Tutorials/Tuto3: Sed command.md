##  Pracatical for sed command

 * For this tutorial we will manupilate file by sed commands.

 * Sed is one of the most used rapid and powerfull unix commands. It stands for "stram eaditor". while it is like grep command, can fetch into files and search for spécified patterns "matching", it can also perform substitution, insertion and deletion functions. Its syntax : 

sed OPTIONS.. [scripts] [Inputfile]
---------------------------------------------------------------------------------------------------------------------------------
#### +++ Introduction : Command's examples : 
---------------------------------------------------------------------------------------------------------------------------------
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

---------------------------------------------------------------------------------------------------------------------------------
#### +++ Printing out practices


* In this tutorial we will be working on a csv file named Laptops.txt 
* Please download the required file into Dir2 whether using wget command or manually from github.
---------------------------------------------------------------------------------------------------------------------------------

1. First let check what our file looks like and how many lines there in? 
<details>
<summary>Answers</summary>

```markdown
cat Laptops.txt
```
```markdown
wc -l Laptops.txt
```
</details>

2. Try this command and figure out what it does mean : 

```markdown
sed '1,5p' Laptops.txt
```

- then print the last lines : use tail command: 

```markdown
tail Laptops.txt
```
<details>
<summary> RQ </summary>
<p>- Notice there is no difference between the two outputs, means the first command printed out all the file.
You could also use this specified command to print all the file : </p>

```markdown
sed -n 'p' Laptops.txt 
```
</details>

3. Add "-n" to sed command then rexecute it; 

```markdown
sed -n '1,5p' Laptops.txt
```

4. Let print lines 1 to 4 , 7 to 9 and 24 : 

```markdown
sed -n '1,4p;7,9p;24p' Laptops.txt 
```

5. Verify your output by comparing to this command which prints number lines. 

```markdown
cat -n Laptops.txt 
```

6. We want to printout some lines with a condition ; first let us choose arbitrary any line, for example line number 13, for this line I'll print out how many character there in : 

```markdown
sed -n '13p' Laptops.txt | wc -m 
```

Now based on this condition we will print lines which equal to, shorter and longer than line n°13:

* line shorter than line n°13 : 

```markdown
sed -n '/^.\{0,49\}$/p' Laptops.txt
```
 
* line equal to line n°13 : 

```markdown
sed -n '/^.\{50\}$/p' Laptops.txt
```

* line longer line n°13 : 

```markdown
sed -n '/^.\{51,\}$/p' Laptops.txt
```

* /^.\{51,\}/: Regular expression pattern we're matching :
* ^: Anchors the pattern to the beginning of the line.
* .: Matches any character.
* \{51,\}: Matches 51 or more occurrences of the preceding character.
* $: Anchors the pattern to the end of the line.

7. let print out odd number lines 

```markdown
sed -n 'p;n’  
```

8. let print out even number lines 

```markdown
sed -n ‘n;p’ 
```
---------------------------------------------------------------------------------------------------------------------------------
#### +++ Substitution : 
---------------------------------------------------------------------------------------------------------------------------------

9. Let substitute "ASUS" by "asus" in Laptops.txt file : 

```markdown
sed 's/ASUS/asus/' Laptops.txt 
```

* Did all the pattern have changed ? (Hint : pipe the previous command to cat command with option -n, look at line 6) 

```markdown
sed 's/ASUS/asus/' Laptops.txt | cat -n 
```

<details>
<summary> Answers </summary>
<p> * Not all patterns change as a result of a substitution because the `sed` command only replaces the first matching occurrence. To replace all the matches to the pattern regardless of the number of times it appears, use the global flag "g": </p>

```markdown
sed 's/ASUS/asus/g' Laptops.txt | cat -n 
```

<p> * Please check line 6 agian </p>
</details>
 
10. Notice that changing "ASUS" to "asus" was done by simply typing the word in lowercase. There are other ways to achieve the same result, such as using a lowercase conversion function or method. 

```markdown
sed 's/ASUS/\L&/g' Laptops.txt 
```

11. Try to change the word "year" to uppercase : 
<details>
<summary> Answers </summary>

```markdown
sed 's/year/\U&/g' Laptops.txt 
```
</details>
 
12. let change the comma separated value to a tab separated value then save it to a new file : 

```markdown
sed 's/,/\t/' Laptops.txt > lap.tsv
```
 
 
