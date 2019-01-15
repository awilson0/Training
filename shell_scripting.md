# Writing shell scripts
Programming can be done one line at a time in the command prompt, or by scripting, where the code is all written beforehand and then run later. Since many bioinformatics tools are run from the command line, I find shell scripting simpler than wrapping the tools into another language like Python or Perl. This tutorial shows some of the utility and features of shell scripting by walking through a common first program – 'Hello World'

## Setting up your script
In your shell type `nano hello_world.sh`. The window will change from the regular shell to a text editor. The bar across the top has the `nano` version and the name of your file: `hello_world.sh`

On the first line of your file, type `#!/usr/bin/bash`. The `#!` symbol (called a 'shebang') tells the shell to send the contents of the file to the program after it. You can find the location of a program with the `which <program>` command. 

## Writing the body of your script
'Hello World' is a simple program that simply prints `Hello World` to the console. The version I'm using here does a few extra things to illustrate some of the more interesting features of shell scripting. 

### 'Hello World' and a brief discussion of documentation
The `echo` command prints the rest of the line to the console, so the basic Hello World program in Unix would look like:
```
#!/usr/bin/bash
echo Hello World #prints 'Hello World' to the console
```
As you can see this is a pretty boring script and it may not seem like there's any reason to even try it. However, I use `echo` quite frequently in my scripts, because it can tell me what step the computer is on. This can be helpful for debugging, or just to see the progress of the script. Another important feature of the simple 'Hello World' script is the comment, denoted by `#`. Comments help make your code more readable to your future self and anyone else who's looking at it. When in doubt, add a comment.

### Environment variables and user inputs
Often you want to write a script that you can run with many different inputs. There are many different ways to do this, but I will only discuss two simple ones. 

The first method is to prompt the user for inputs at the beginning of the script. The responses will be stored in variables that are accessible to the script but not outside of it.
```
#!/usr/bin/bash
echo What is your name? #Ask the user for their name
read user #Store the keyboard input in the variable $user
echo Hello, $user #Prints 'Hello, (value of user)' to the console
```
The other method is to set the variables as environment variables before running the script. You can run `export NAME=Andrew` to assign the value 'Andrew' to an environment variable called NAME. If NAME already exists, it's value will change to 'Andrew' and if it doesn't exist, it will be created. Once the environment variable exists, it can be called by the shell script.
```
#!/usr/bin/bash
echo Hello, $NAME #Prints 'Hello, (value of the NAME variable)' to the console
```

### Looping
One of the most powerful features of a shell script is that you can loop through multiple files without having to write code each time.
```
#!/usr/bin/bash
for name in Person1 Person3 ... Person5 # The code between 'do' and 'done' will be executed for different values of $name
do
echo Hello, $name
done
```
