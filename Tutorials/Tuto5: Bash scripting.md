##  Pracatical for Bash Scripting

---------------------------------------------------------------------------------------------------------------------------------
#### +++ What is a Bash : 
---------------------------------------------------------------------------------------------------------------------------------
 * A Bash stands for "short for Bourne Again SHell",  is a command-line shell and scripting language commonly used in Unix and Linux environments to chain a few shell commands together in a file for ease of use.
 * It provides a powerful interface for interacting with your operating system and automating tasks.

---------------------------------------------------------------------------------------------------------------------------------
#### +++ How to write a bash script
---------------------------------------------------------------------------------------------------------------------------------
It is crucial to know tha a bash script involves creating a text file containing a series of Bash commands and instructions. So here's a step-by-step guide on how to write a basic Bash script:
 
* First create a Directory called script under letsPractice; (pwd : ~/letsPractice/scripts).

- **Step** 1: Open a Text Editor;
  * Start by opening a text editor of your choice. You can use command-line editors like nano or graphical editors like Visual Studio Code, Sublime Text, or Notepad++ any text editor of your choice. 
  * For this example, let's assume you're using a simple command-line editor like nano.
    
```markdown 
nano my_first_script.sh
```

  * The **.sh** extension refers to the scripting language commands file that contains computer program to be run by Unix shell.
  
- **Step** 2: Write a Shebang Line;
  * The first line is often called the "shebang" line. It specifies the interpreter that should be used to execute the script. 
  * For Bash, the shebang line is:
  
```markdown 
#!/bin/bash
```

- **Step** 3: Write your first Bash Command;
  * Echo is one of the basic Unix/Linux command in linux and most commonly used in shell scripts, it is used for displaying lines of text or string which are passed as arguments on the command line.
  
```markdown 
echo " If you don't practice you don't deserve to win"
```

- **Step** 4: Add Comments to your bash file;
  * To describe what your script does or to provide context for others users, you may add a non-excuted lines which serves to explain or to provide a documentation. 
  * Comments starts with a " # " symbol.

```markdown 
# This is test comment
```

- **Step** 5: Save your Script (your file);
  * Hint : In nano, you can press Ctrl + O, then press Enter to confirm the file name and save it. To exit nano, press Ctrl + X.

- **Step** 6: Make your Script Executable
  * Note that until now you just created an usual file which contains sentences but still undefined as command to be executed. So before you can run the script, you need to make it executable.
  * Navigate to the directory where your script is located, then type; 
  
```markdown
ls -l
```

- Your output will seems like : -rw-rw-r-- 1 user1 users size  Month day time  filename
<details> 
<summary> Explanation </summary>
<p> - The first column stands for :File Type and Permissions: consists of ten characters, which include information about read "r", write "w" and execute "x" permissions for the owner "u", group "g" , and others "o", as well as special file types.</p>
<p> - The second column stands for :Number of Hard Links: associated with the file or directory.</p>
<p> - The third column stands for :Owner: of the file or directory.</p>
<p> - The fourth column stands for :Group: associated with the file or directory.</p>
<p> - The fifth column stands for :File Size: in bytes.</p>
<p> - The sixth column stands for the last :Modification Time: of the file or directory.</p>
<p> - The last column stands for :File/Directory: Name.</p>
</details>

- Note that there is no execute option neither for owner, group or others. So to change the permission we will use the "chmod" command as follows; 

```markdown 
chmod a+x my_first_script.sh
```

- Now type againe ls -l  what do you notice ? 
<details> 
<summary> Change Permissions using the symbolic mode </summary>
<p>- Use “u” for users, "g for group, "o" for others, and "ugo" or "a" (for all).</p>
<p>- To give permission use "+" , To take it use "-".</p>

```markdown 
chmod a-x my_first_script.sh
```

</details>
<details> 
<summary> Changing permissions in numeric code </summary>
- To do this you use numbers instead of "r", "w", or "x" :

- 0 = No Permission
- 1 = Execute
- 2 = Write
- 4 = Read

So you  may add up the numbers depending on the level of permission you want to give.

- 0 = ---
- 1 = --x
- 2 = -w-
- 3 = -wx
- 4 = -r-
- 5 = r-x
- 6 = rw-
- 7 = rwx

For example ;
   - To give write,reade an exexute permission  for all you may type : 

```markdown 
chmod 777 my_first_script.sh
```

   - To give read, write, and execute permissions for the user only, type : 

```markdown 
chmod 700 my_first_script.sh
```
 
   - To give write and execute (3) permission for the user(owner), w (2) for the group, and read, write, and execute for the users, type : 

```markdown 
chmod 327 my_first_script.sh
```

</details>
 
- **Step** 7: Run your script;
There many method to run you script, 
- First method :

```markdown 
bash my_first_script.sh
```

- The second method is : 

```markdown 
./my_first_script.sh 
```

- Third method : 

```markdown 
source my_first_script.sh 
```

- **Step** 8:  Run your script elsewhere other than your original directory;
  - Temporary:
* First check your current working directory path.

```markdown 
pwd 
```

* Add the directoty to the PATH temporarily (only for the current session), you can use the following command:

```markdown 
export PATH=$PATH:/your/directory/path
```
* Now you may simply type your name script then it will be executed:

```markdown
my_first_script
```

  - Permanently
* If you want to make the change permanent, you need to add the export command to one of your shell's configuration files:

```markdown 
echo 'export PATH=$PATH:/your/directory/path' >> ~/.bashrc
```

* Then 
```markdown 
source ~/.bashrc
```

* Now you can notice that th command " export PATH=$PATH:/your/directory/path " was appended to the last line in .barshrc file then it may be executed anywere.

* Try to change your directory or exit from the terminal then open it, then execute your script it should run properly.

