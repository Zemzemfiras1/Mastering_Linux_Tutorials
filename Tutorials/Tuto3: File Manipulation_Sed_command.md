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

---------------------------------------------------------------------------------------------------------------------------------
#### Printing out practices


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

6. 






















