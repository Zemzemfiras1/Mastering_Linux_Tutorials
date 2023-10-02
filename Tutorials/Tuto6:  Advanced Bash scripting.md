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

###### Exercise 1 : Write a  Bash script that print human-readable and long listing format files. ( Hint: use man ls ). 
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

###### Exercise 2: Write a  Bash script that print human-readable and long listing format files. ( Hint: use man ls ). 
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
#### +++ How to create an interactive input
---------------------------------------------------------------------------------------------------------------------------------
###### Exercise 3: Create a bash script which demand the name of the user.

* Here we will use "read" command which is used to read input from the user or from a file. It is often used in shell scripts to assign values to variables, read user input interactively, or process lines from files. 

1. create your script file: 

```markdwon 
nano script3.sh 
```

2. copy this script then save and run it. 

```markdown
#!/bin/bash
# Prompt the user for their name
echo "Please enter your name: "
read name
echo "Hello, $name!"
```

* In this example, the read command waits for the user to enter their name, and the entered value is stored in the name variable for later use.
###### Exercise 4: Add age variable to read command. 
3. change your script to be as bellow : 

```markdown 
#!/bin/bash
# Prompt for name and age
echo "Enter your name and age: "
read name age
echo "Hello, $name! You are $age years old."
```

###### Exercise 5:  Enter a list of number. 
* The -a option allows you to read input into an array. 
* The user can enter numbers separated by spaces, and they will be stored in the numbers array.

```markdown
nano script5.sh
```

```markdown
#!/bin/bash
# Read a list of numbers into an array
echo "Enter a list of numbers separated by spaces: "
read -a numbers
echo "You entered: ${numbers[@]}"
```

---------------------------------------------------------------------------------------------------------------------------------
#### +++ Conditions in bash scripting 
---------------------------------------------------------------------------------------------------------------------------------
###### Exercise 6: Create a bash script which demand a number as input then detect its sign. 

```markdown
nano script6.sh
```

```markdown
#!/bin/bash

# Prompt the user for input
read -p "Enter a number: " num

# Check if the entered number is less than 0
if [ $num -lt 0 ]; then
    echo "$num is a negative number."
else
    echo "$num is a positive number."
fi
```

* read -p "Enter a number: " num ,  prompts the user to enter a number and stores the input in the num variable.
* if [ $num -lt 0 ]; then , starts an if statement that checks whether the value stored in num is less than 0.
* echo "$num is a negative number." , is the code that executes if the condition in the if statement is true. It prints a message indicating that the number is negative.
* else marks the beginning of the code to be executed if the condition in the if statement is false.
* echo "$num is a positive number." , is the code that executes if the condition in the if statement is false. It prints a message indicating that the number is positive.

<details>
<summary> Bash script Comparison operators for numeric values in conditional statements </summary> 
<p>- Equality (-eq): Check if the first number is equal to the second number.</p>
<p>- Inequality (-ne): Check if the first number is not equal to the second number.</p>
<p>- Less than (-lt): Check if the first number is less than the second number.</p>
<p>- Less than or equal to (-le): Check if the first number is less than or equal to the second number.</p>
<p>- Greater than (-gt): Check if the first number is greater than the second number.</p>
<p>- Greater than or equal to (-ge): Check if the first number is greater than or equal to the second number.</p>
</details>

###### Exercise 7: Create a bash script which compare two numbers. 
1. create your script file: 

```markown 
nano script7.sh
```

2. copy this script then save and run it. 

```markdown
#!/bin/bash

# Prompt the user for two numbers
read -p "Enter the first number: " num1
read -p "Enter the second number: " num2

# Check if the input is numeric
if ! [[ "$num1" =~ ^[0-9]+$ ]] || ! [[ "$num2" =~ ^[0-9]+$ ]]; then
    echo "Error: Please enter valid numeric values."
    exit 1
fi

# Perform numeric comparisons
if [ "$num1" -eq "$num2" ]; then
    echo "$num1 is equal to $num2"
elif [ "$num1" -lt "$num2" ]; then
    echo "$num1 is less than $num2"
elif [ "$num1" -le "$num2" ]; then
    echo "$num1 is less than or equal to $num2"
elif [ "$num1" -gt "$num2" ]; then
    echo "$num1 is greater than $num2"
elif [ "$num1" -ge "$num2" ]; then
    echo "$num1 is greater than or equal to $num2"
fi
```


---------------------------------------------------------------------------------------------------------------------------------
#### +++ While loop
---------------------------------------------------------------------------------------------------------------------------------
###### Exercise 8: Create a bash script which countdown from a specified number to 1 
1. create your script file: 

```markown 
nano script8.sh
```

2. copy this script then save and run it. 

```markown 
#!/bin/bash

# Prompt the user for a positive integer
read -p "Enter a positive integer: " num

# Check if the input is a valid positive integer
if ! [[ "$num" =~ ^[1-9][0-9]*$ ]]; then
    echo "Error: Please enter a valid positive integer."
    exit 1
fi

echo "Counting down from $num to 1:"
while [ "$num" -gt 0 ]; do
    echo "$num"
    num=$((num - 1))
done

echo "Countdown complete!"
```

---------------------------------------------------------------------------------------------------------------------------------
#### +++ For loop
---------------------------------------------------------------------------------------------------------------------------------
###### Exercise 9: Create a bash script which count from 1 to a specified number.

```markown 
nano script9.sh
```

2. copy this script then save and run it. 

```markown 
#!/bin/bash

# Prompt the user for a positive integer
read -p "Enter a positive integer: " num

# Check if the input is a valid positive integer
if ! [[ "$num" =~ ^[1-9][0-9]*$ ]]; then
    echo "Error: Please enter a valid positive integer."
    exit 1
fi

echo "Counting from 1 to $num:"
for ((i = 1; i <= num; i++)); do
    echo "$i"
done

echo "Counting complete!"
```

---------------------------------------------------------------------------------------------------------------------------------
#### +++ Others sources
---------------------------------------------------------------------------------------------------------------------------------
- [What is a bash script?](https://ryanstutorials.net/bash-scripting-tutorial/bash-script.php)
- [Bash scripting tutorials](https://linuxconfig.org/bash-scripting-tutorial-for-beginners)
- [30 Bash Script Examples](https://linuxhint.com/30_bash_script_examples/)



