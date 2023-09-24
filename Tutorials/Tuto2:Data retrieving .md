## Mv, cp, wc, cat, more, less, grep commands




1. We want to move the directory Dir4 located in letsPractice into Dir1 as a subdirectory. 
   For this step we will use the same command move " mv " used previously in names changing. 
   * if your current working directory was letspractice you can simply type: 
        
```markdown
mv Dir4 Dir1/ 
```

  => Here we specified the file then the final path
   * Or if you were in your final path, both initial and final path shoud be written; 
   
```markdown     
mv ~/letsPractive/Dir4 . 
```
   or
   
```markdown
mv ../Dir4 .     
```
  => The . refers to your current working directory.
  
  =>    .. refers to parent directory.
  
2. Rename Dir4 to tuto2. **Hint:** Use mv command.

3. Copy file2 into tuto2. 
   * If you are located in tuto2 directory you could type ;
   
```markdown     
cp ~/letsPractice/Dir1/file2.txt ~/letsPractice/Dir1/tuto2/
```   
   or
   
```markdown     
cp ../file2.txt .
```
else if you are where the file you want to copy ;

```markdown      
cp file2.txt tuto2/
```
4. let us get some details about this file, how many lines? words? and its size ? **Use** use wildcards command, to see more options check the manual.

```markdown
man wc 
```

<details>
<summary>Answer</summary>

```markdown
wc file2.txt
```
or specifically 

```markdown
wc -l file.txt
```
```markdown
wc -w file.txt
```
```markdown
wc -c file.txt
```
</details>
   
5. For more advanced commands, first let download Path_to_succes.txt from github: simply use **wget** command and link's file; 

```markdown
wget https://github.com/Zemzemfiras1/Mastering_Linux_Tutorials/blob/master/First%20tutorial/Path_to_success.txt
```
6. How Many words and lines contains the file?

7. To inspect the file contents, try more, less, cat commands.
 
   * Try man command to know what difference between those commands. 
   * Read descpription section.
  
<details>
<summary>Commands</summary>

```markdown
more Path_to_success.txt
```
```markdown
less Path_to_success.txt
```
```markdown
cat Path_to_success.txt
```
</details>
     
8. Knowing that Path_to_succes.txt contains many chapters. so instead of fetching the file and scrolling down, simply we can use grep "global regular expression print" which is a powerful command used to search for matching patterns is a file. 
```markdown   
grep "Chapter" Path_to_success.txt
```
9. How many matched patterns there is in Path_to_success.txt

<details>
<summary>Answers</summary>

```markdown
grep "success" Path_to_success.txt 
```
* Notice that this command print out lines containing success. So to verify lines numbers just add " -n " option; 
```markdown
grep -n "success" Path_to_success.txt 
```
* Remember that previously we used wc command to print out number of lines so lets try it ;

```markdown
grep -n "success" Path_to_success.txt | wc
``` 

```markdown
grep "success" Path_to_success.txt | wc
```

* <p> The symbol " | " is called piping , it means we piped the output of the first command to the input of the second command.</p>
* <p> Unfortunately it does not work as we want for the reason each paragraph is considered as a line. </p>

<details>
<summary> Check manual to know what means the option -o</summary>

```markdown
man grep
```

<details>
<summary>Correct command is :</summary>

```markdown
grep -o "success" Path_to_success.txt 
```
```markdown
grep -n -o "success" Path_to_success.txt 
```
```markdown
grep -n -o "success" Path_to_success.txt |wc 
```
* <p>Note that "-o" and "wc" option is enough for the counting. we wanted to check that we can mixte options and commands.</p>
</details> 
</details>
</details>

 
