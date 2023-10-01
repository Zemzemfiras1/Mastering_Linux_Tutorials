##  Pracatical for Advanced Bash Scripting


---------------------------------------------------------------------------------------------------------------------------------
#### +++ Create a simple function: 
---------------------------------------------------------------------------------------------------------------------------------
 * To reuse code written in your script, function will offer you a perfect organisation. 
 * Function are organaised as bellow : 
 
```
function_name() {
    - Function body
    - Commands and statements go here
    - You can use parameters passed to the function as $1, $2, etc.
}
```

###### Exercice1 : Write a  Bash script that print human-readable and long listing format files. ( Hint: use man ls ). 
#!/bin/bash
1. create your script file: 

```markdwon 
nano script1.sh 
```

2. Write or copy this syntax in your file. 

```markdown
# Define a function called my_function
my_function() {
    echo "If you don't practice you don't deserve to win" #The executed command
}

# Call for my_function
my_function
```

3. Make your script executable Than run it. 

###### Exercice2 : Write a  Bash script that print human-readable and long listing format files. ( Hint: use man ls ). 
1. create your script file: 

```markdwon 
nano script2.sh 
```

2. Write or copy this syntax in your file. 

```markdown
#!/bin/bash

# Create a function named my_ls
my_ls () {
    command ls -lh #The executed command
}

# A call for the function
my_ls
```

3. Make your script executable Than run it. 

---------------------------------------------------------------------------------------------------------------------------------
#### +++ How an interactive input
---------------------------------------------------------------------------------------------------------------------------------

