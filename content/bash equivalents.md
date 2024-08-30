---
dg-publish: true
dg-show-toc: true
---

Examples of bash commands and how to do the same thing in PowerShell

# Echo

Write text to the screen.

- **Bash**
    ```bash
    echo "Hello, World!"
    echo -e "Hello, \t World!"
    ```

- **PowerShell**
    ```powershell
    Write-Output 'Hello, World!'
    Write-Output "Hello, `t World!"
	```
	> Dirty version:  
	> `echo 'Hello, World!'`

# Execute a Script

Save and execute a script with bash and PowerShell.

- **Bash**  
    Assume that `echo1.sh` has the following contents.
    ```bash
    echo "Hello, World!"
    ```

    You would the execute it with the following command line.
    ```bash
    bash echo1.sh
    ```

- **PowerShell**  
    Assume `echo1.ps1` has the following contents.
    ```powershell
    Write-Output "Hello, World!"
    ```

    You would then execute it with the following command line.
    ```bash
    pwsh echo1.ps1
    ```

# Comments

Comments are the same in PowerShell and bash.

- **Bash**  
	```bash
	# My Comment!
	```

- **PowerShell**  
	```powershell
	# My Comment!
	```

# Multiline Comments

Multiline comments are different between bash and PowerShell.

- **Bash**  
	```bash
	: 'Multi
	line
	comment'
	echo "42"
	```

- **PowerShell**  
	```powershell
	<# 
	Multi
	line
	comment
	#>
	Write-Output "42"
	```

# While Loop

- **Bash**  
	```bash
	valid=true
	count=1
	while [ $valid ]
	do
	echo $count
	if [ $count -eq 5 ];
	then
	break
	fi
	((count++))
	done
	```

- **PowerShell**  
	```powershell
	$count = 0
	while ($true) {
	  Write-Host $count
	  if ($count -eq 5) {
	      break
	  }
	  $count++
	}
	```

# For Loop

- **Bash**  
	```bash
	for (( counter=10; counter>0; counter-- ))
	do
	echo -n "$counter "
	done
	```

- **PowerShell**  
	```powershell
	for ($counter = 10; $counter -gt 0; $counter--) {
	    Write-Host $counter
	}
	```

# Get User Input

- **Bash**  
	```bash
	echo "Enter Your Name"
	read name
	echo "Welcome, $name!"
	```

- **PowerShell**
    ```powershell
    $name = Read-Host "Enter Your Name"
    Write-Host "Welcome, $name!"
    ```

# If Statement

- **Bash**  
	```bash
	n=10
	if [ $n -lt 10 ];
	then
	echo "It is a one digit number"
	else
	echo "It is a two digit number"
	fi
	```

- **PowerShell**  
	```powershell
	$n = 10
	if ($n -lt 10) {
	    Write-Host "It is a one digit number"
	} else {
	    Write-Host "It is a two digit number"
	}
	```

# If with And Logic

- **Bash**  
	```bash
	echo "Enter username"
	read username
	echo "Enter password"
	read password
	
	if [[ ( $username == "admin" &amp;&amp; $password == "secret" ) ]]; then
	echo "valid user"
	else
	echo "invalid user"
	fi
	```

- **PowerShell**  
	```powershell
	$UserName = Read-Host "Enter username"
	$Password = Read-Host "Enter password"
	
	if ($username -eq 'admin' -and $password -eq 'secret') {
	    Write-Host 'valid user'
	} else {
	    Write-Host 'invalid user'
	}
	```

# If with Or Logic

- **Bash**  
	```bash
	echo "Enter any number"
	read n
	
	if [[ ( $n -eq 15 || $n  -eq 45 ) ]]
	then
	echo "You won the game"
	else
	echo "You lost the game"
	fi
	```

- **PowerShell**  
	```powershell
	[int]$n = Read-Host "Enter any number"
	
	if ($n -eq 15 -or $n -eq 45) {
	    Write-Host "You won the game"
	} else {
	    Write-Host "You lost the game"
	}
	```

# If Else Statements

- **Bash**  
	```bash
	echo "Enter your lucky number"
	read n
	
	if [ $n -eq 101 ];
	then
	echo "You got 1st prize"
	elif [ $n -eq 510 ];
	then
	echo "You got 2nd prize"
	elif [ $n -eq 999 ];
	then
	echo "You got 3rd prize"
	
	else
	echo "Sorry, try for the next time"
	fi
	```

- **PowerShell**  
	```powershell
	[int]$n = Read-Host "Enter your lucky number"
	
	if ($n -eq 101) {
	    Write-Host "You got 1st prize"
	} elseif ($n -eq 510) {
	    Write-Host "You got 2nd prize"
	} elseif ($n -eq 999) {
	    Write-Host "You got 3rd prize"
	} else {
	    Write-Host "Sorry, try for the next time"
	}
	```

# Case Statement

- **Bash**  
	```bash
	echo "Enter your lucky number"
	read n
	case $n in
	101)
	echo "You got 1st prize" ;;
	510)
	echo "You got 2nd prize" ;;
	999)
	echo "You got 3rd prize" ;;
	*)
	echo "Sorry, try for the next time" ;;
	esac
	```

- **PowerShell**  
	```powershell
	[int]$n = Read-Host "Enter your lucky number"
	switch($n) {
	    101 { Write-Host "You got 1st prize" }
	    510 { Write-Host "You got 2nd prize" }
	    999 { Write-Host "You got 3rd prize" }
	    default { Write-Host "Sorry, try for the next time" }
	}
	```

# Command Line Arguments

- **Bash**  
	```bash
	echo "Total arguments : $#"
	echo "1st Argument = $1"
	echo "2nd argument = $2"
	```

- **PowerShell**  
	```powershell
	Write-Host "Total arguments: $($args.Length)"
	Write-Host "1st Argument: $($args[0])"
	Write-Host "2nd Argument: $($args[1])"
	```

# Named Command Line Arguments

- **Bash**  
	```bash
	for arg in "$@"
	do
	index=$(echo $arg | cut -f1 -d=)
	val=$(echo $arg | cut -f2 -d=)
	case $index in
	X) x=$val;;
	
	Y) y=$val;;
	
	*)
	esac
	done
	((result=x+y))
	echo "X+Y=$result"
	```

- **PowerShell**  
	```powershell
	param([int]$X, [int]$Y)
	
	$Result = $X + $Y
	Write-Host "X+Y=$Result"
	```

# Concatenating Strings

- **Bash**  
	```bash
	string1="Linux"
	string2="Hint"
	echo "$string1$string2"
	string3=$string1+$string2
	string3+=" is a good tutorial blog site"
	echo $string3
	```

- **PowerShell**  
	```powershell
	$string1 = "Ironman"
	$string2 = "Software"
	Write-Host "$string1$string2"
	$string3 = $string1+$string2
	$string3 +=" makes good software"
	Write-Host $string3
	```

# Substring of a String

- **Bash**  
	```bash
	Str="Learn Linux from LinuxHint"
	subStr=${Str:6:5}
	echo $subStr
	```

- **PowerShell**  
	```powershell
	$Str = 'Learn PowerShell from Ironman Software'
	$subStr = $Str.Substring(6, 10)
	Write-Host $subStr
	```

# Functions

- **Bash**  
	```bash
	function F1()
	{
	echo 'I like bash programming'
	}
	
	F1
	```

- **PowerShell**  
	```powershell
	function F1 {
	    Write-Host "I like PowerShell programming"
	}
	F1
	```

# Functions with Parameters

- **Bash**  
	```bash
	Rectangle_Area() {
	area=$(($1 * $2))
	echo "Area is : $area"
	}
	
	Rectangle_Area 10 20
	```

- **PowerShell**  
	```powershell
	function RectangleArea {
	    $Area = $Args[0] * $Args[1]
	    Write-Host "Area is: $Area"
	}
	RectangleArea 10 20
	```

# Use the Return value of a Function

- **Bash**  
	```bash
	function greeting() {
	
	str="Hello, $name"
	echo $str
	
	}
	
	echo "Enter your name"
	read name
	
	val=$(greeting)
	echo "Return value of the function is $val"
	```

- **PowerShell**  
	```powershell
	function Greeting {
	    "Hello, $Name"
	}
	
	$Name = Read-Host "Enter your name"
	$Val = Greeting
	Write-Host "Return value of the function is $val"
	```

# Make a Directory

- **Bash**  
	```bash
	echo "Enter directory name"
	read newdir
	`mkdir $newdir`
	```

- **PowerShell**  
	```powershell
	$newdir = Read-Host "Enter directory name"
	New-Item $newdir -ItemType Directory
	```
	> Dirty version:  
	> `mkdir $newdir`

# Make Directory if it doesn’t exist

- **Bash**  
	```bash
	echo "Enter directory name"
	read ndir
	if [ -d "$ndir" ]
	then
	echo "Directory exist"
	else
	`mkdir $ndir`
	echo "Directory created"
	fi
	```

- **PowerShell**  
	```powershell
	$newdir = Read-Host "Enter directory name"
	if (Test-Path $newdir)
	{
	    Write-Host "Directory exists"
	} else {
	    New-Item $newdir -ItemType Directory
	}
	```
	> Dirty version:  
	> `$newdir = Read-Host "Enter directory name"`  
	> `if (gi $newdir -ea si)`  
	> `{`  
	> `    echo "Directory exists"`  
	> `} else {`  
	> `    mkdir $newdir`  
	> `}`  

# Read a File

- **Bash**  
	```bash
	file='book.txt'
	while read line; do
	echo $line
	done < $file
	```

- **PowerShell**  
	```powershell
	Get-Content 'book.txt'
	```

# Delete a File

- **Bash**  
	```bash
	echo "Enter filename to remove"
	read fn
	rm -i $fn
	```

- **PowerShell**  
	```powershell
	$fn = Read-Host "Enter a file to remove"
	Remove-Item $fn
	```
	> Dirty version:  
	> `$fn = Read-Host "Enter a file to remove"`  
	> `rm $fn`  

# Append to a File

- **Bash**  
	```bash
	echo "Before appending the file"
	cat book.txt
	
	echo "Learning Laravel 5">> book.txt
	echo "After appending the file"
	cat book.txt
	```

- **PowerShell**  
	```powershell
	Write-Host "Before appending the file"
	Get-Content book.txt
	
	"Learning Laravel 5" >> book.txt
	Write-Host "After appending the file"
	Get-Content book.txt
	```

# Wait for a Process

- **Bash**  
	```bash
	echo "Wait command" &amp;
	process_id=$!
	wait $process_id
	echo "Exited with status $?"
	```

- **PowerShell**
	```powershell
	Start-Process notepad -Wait
	Get-Process -Id $ProcessId | Wait-Process
	```

# Sleep

- **Bash**  
	```bash
	echo “Wait for 5 seconds”
	sleep 5
	echo “Completed”
	```

- **PowerShell**  
	```powershell
	Write-Host "Wait for 5 seconds"
	Start-Sleep 5 
	```
	> Dirty version:  
	> `sleep 5`  
	> `Write-Host "Completed"`  

# Download Files

- **Bash**  
	```bash
	curl -o newname.txt http://www.het.brown.edu/guide/UNIX-password-security.txt
	```

- **PowerShell**  
	```powershell
	Invoke-WebRequest http://www.het.brown.edu/guide/UNIX-password-security.txt -OutFile .\newname.txt
	```
	> Dirty version:  
	> `iwr http://www.het.brown.edu/guide/UNIX-password-security.txt -o newname.txt`  
	```



# Search a File for a String

- **Bash**
	```bash
	error log.txt     # Search a file
	grep error *      # Search a directory
	grep -r error *   # Recursively search a directory
	grep -l error *   # List matching files
	grep -c error *   # Measure number of objects
	grep -C 2 error * # Display lines before and after
	```

- **PowerShell**
	```powershell
	Select-String error log.txt                     # Search a file
	Select-String error *                           # Search a Directory
	Get-ChildItem * -Recurse | Select-String error  # Recursively search a directory
	Select-String error * | Select-Object path      # List matching files
	Select-String error * | Measure-Object          # Count Matches
	Select-String error *                           # Display lines before and after
	```


---


Sources:
- 2021-12-09: [Bash vs PowerShell Cheat Sheet](https://blog.ironmansoftware.com/daily-powershell/bash-powershell-cheatsheet/)
- 2021-12-09: [30 Bash Script Examples](https://linuxhint.com/30_bash_script_examples/)

Related:
[Shell, Bash - The Linux command line](Shell,%2520Bash%2520-%2520The%2520Linux%2520command%2520line.md#)

Tags:
[PowerShell - A command-line shell and scripting language to manage Windows system and automate administrative tasks](./powershell.md)