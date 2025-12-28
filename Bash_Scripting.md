
---

# 🐚 Bash Scripting — Complete Syntax & Concepts Guide

## 📘 Overview

Bash (**Bourne Again Shell**) is the most common Unix/Linux shell used for automation, backend scripting, and system administration.
This document covers **all major syntax and concepts** you need to write, debug, and optimize Bash scripts.

---

## 🧩 Table of Contents

- [🐚 Bash Scripting — Complete Syntax \& Concepts Guide](#-bash-scripting--complete-syntax--concepts-guide)
  - [📘 Overview](#-overview)
  - [🧩 Table of Contents](#-table-of-contents)
  - [🟢 Getting Started](#-getting-started)
  - [🔠 Basic Syntax](#-basic-syntax)
  - [🧮 Variables](#-variables)
  - [🧑‍💻 User Input](#-user-input)
  - [➕ Operators](#-operators)
    - [Example Usage in Bash](#example-usage-in-bash)
  - [🔀 Conditionals (if / else / case)](#-conditionals-if--else--case)
  - [🔁 Loops (for / while / until)](#-loops-for--while--until)
    - [For loop](#for-loop)
    - [While loop](#while-loop)
    - [Until loop](#until-loop)
  - [🧩 Functions](#-functions)
  - [🧠 Arrays](#-arrays)
  - [🔤 String Operations](#-string-operations)
  - [📁 File Operations](#-file-operations)
  - [🔄 Input / Output Redirection](#-input--output-redirection)
  - [🧳 Command-Line Arguments](#-command-line-arguments)
  - [⚠️ Error Handling](#️-error-handling)
  - [⚙️ Process Management](#️-process-management)
  - [⏰ Scheduling with Cron](#-scheduling-with-cron)
  - [🌍 Environment Variables](#-environment-variables)
  - [🐞 Debugging](#-debugging)
  - [✅ Best Practices](#-best-practices)
  - [🧱 Example: Deployment Script](#-example-deployment-script)
  - [📚 References](#-references)

---

## 🟢 Getting Started

To create a Bash script:

```bash
#!/bin/bash
# My first script
echo "Hello, Backend!"
```

Make it executable:

```bash
chmod +x script.sh
./script.sh
```

---

## 🔠 Basic Syntax

* Comments start with `#`
* Commands are separated by newlines or `;`
* Indentation is not required (but recommended)

Example:

```bash
# Single line command
echo "Hello"; echo "World"
```

---

## 🧮 Variables

Define variables without spaces:

```bash
name="Bash"
age=10
```

Access variables:

```bash
echo "Shell: $name, Version: $age"
```

Constant variables (readonly):

```bash
readonly PI=3.14
```

Unset variable:

```bash
unset name
```

---

## 🧑‍💻 User Input

```bash
read -p "Enter your username: " user
echo "Welcome, $user!"
```

---

## ➕ Operators

Arithmetic:

```bash
a=5; b=3
echo $((a + b))  # 8
echo $((a * b))  # 15
```

String comparison:

```bash
if [ "$a" = "$b" ]; then
  echo "Equal"
fi
```
---

Arithmetic Conditional Operators 

Arithmetic conditional operators are used to **compare two numbers** and return **true or false**.

| Operator | Meaning               | Example         | Description                         |
| -------- | --------------------- | --------------- | ----------------------------------- |
| `-lt`    | Less than             | `[ 5 -lt 10 ]`  | True if 5 is less than 10           |
| `-gt`    | Greater than          | `[ 10 -gt 5 ]`  | True if 10 is greater than 5        |
| `-le`    | Less than or equal    | `[ 5 -le 5 ]`   | True if values are equal or less    |
| `-ge`    | Greater than or equal | `[ 10 -ge 10 ]` | True if values are equal or greater |
| `-eq`    | Equal to              | `[ 5 -eq 5 ]`   | True if both values are equal       |
| `-ne`    | Not equal to          | `[ 5 -ne 10 ]`  | True if values are not equal        |

---

### Example Usage in Bash

```bash
num1=10
num2=5

if [ $num1 -gt $num2 ]; then
  echo "num1 is greater than num2"
fi
```

---


File tests:

```bash
[ -f "file.txt" ]   # True if file exists
[ -d "dir" ]        # True if directory exists
[ -r "file" ]       # Readable
[ -w "file" ]       # Writable
[ -x "file" ]       # Executable
```

---

## 🔀 Conditionals (if / else / case)

```bash
if [ "$age" -ge 18 ]; then
  echo "Adult"
elif [ "$age" -ge 13 ]; then
  echo "Teen"
else
  echo "Child"
fi
```

Case statement:

```bash
case "$day" in
  "Mon") echo "Start of week";;
  "Fri") echo "Weekend soon";;
  *) echo "Regular day";;
esac
```

---

## 🔁 Loops (for / while / until)

### For loop

```bash
for i in {1..5}; do
  echo "Count: $i"
done
```

### While loop

```bash
count=1
while [ $count -le 5 ]; do
  echo "Count: $count"
  ((count++))
done
```

### Until loop

```bash
until [ $count -gt 5 ]; do
  echo "Count: $count"
  ((count++))
done
```

---

## 🧩 Functions

```bash
greet() {
  echo "Hello, $1!"
}
greet "Backend Dev"
```

Return values:

```bash
add() {
  echo $(( $1 + $2 ))
}
result=$(add 5 10)
echo "Sum = $result"
```

---

## 🧠 Arrays

Declare and access:

```bash
arr=(apple banana cherry)
echo ${arr[1]}       # banana
echo ${arr[@]}       # all items
echo ${#arr[@]}      # length
```

Loop through array:

```bash
for fruit in "${arr[@]}"; do
  echo "$fruit"
done
```

---

## 🔤 String Operations

```bash
text="backend"
echo ${#text}           # Length
echo ${text:0:4}        # Substring -> back
echo ${text/back/front} # Replace
```

---

## 📁 File Operations

```bash
touch file.txt
echo "Hello" > file.txt
cat file.txt
rm file.txt
```

Append to file:

```bash
echo "Log entry" >> logs.txt
```

---

## 🔄 Input / Output Redirection

| Symbol | Meaning                     |
| ------ | --------------------------- |
| `>`    | Redirect output (overwrite) |
| `>>`   | Append output               |
| `<`    | Redirect input              |
| `2>`   | Redirect error              |
| `&>`   | Redirect stdout and stderr  |

Example:

```bash
command > output.log 2>&1
```

---

## 🧳 Command-Line Arguments

```bash
#!/bin/bash
echo "Script: $0"
echo "First: $1"
echo "Second: $2"
echo "All args: $@"
echo "Count: $#"
```

---

## ⚠️ Error Handling

Stop script on first error:

```bash
set -e
```

Custom error messages:

```bash
if ! cp file.txt /backup; then
  echo "Backup failed!" >&2
  exit 1
fi
```

---

## ⚙️ Process Management

```bash
ps aux | grep python
kill -9 <pid>
nohup python3 app.py &
```

Get PID:

```bash
echo "Process ID: $$"
```

---

## ⏰ Scheduling with Cron

Edit crontab:

```bash
crontab -e
```

Example (run every midnight):

```bash
0 0 * * * /home/user/scripts/backup.sh
```

---

## 🌍 Environment Variables

List all:

```bash
printenv
```

Set and export:

```bash
export DB_USER="admin"
```

Use in scripts:

```bash
echo "Connecting as $DB_USER"
```

---

## 🐞 Debugging

Run in debug mode:

```bash
bash -x script.sh
```

Add debugging in code:

```bash
set -x   # start debug
# commands
set +x   # stop debug
```

---

## ✅ Best Practices

✔ Always start with `#!/bin/bash`
✔ Use `set -e` to stop on errors
✔ Quote variables `"$var"`
✔ Use functions for modularity
✔ Validate input
✔ Write logs
✔ Use descriptive variable names
✔ Comment complex sections

---

## 🧱 Example: Deployment Script

```bash
#!/bin/bash
set -e

APP_DIR="/var/www/backend"
LOG_FILE="/var/log/deploy.log"

echo "Deploying app..." | tee -a $LOG_FILE
cd $APP_DIR
git pull origin main
systemctl restart backend.service
echo "Deployment complete at $(date)" | tee -a $LOG_FILE
```

---

## 📚 References

* [GNU Bash Manual](https://www.gnu.org/software/bash/manual/)
* [Linux Command Cheat Sheet](https://cheatography.com/davechild/cheat-sheets/linux-command-line/)
* [Advanced Bash Guide](https://tldp.org/LDP/abs/html/)
