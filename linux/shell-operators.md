# Shell Operators

Shell operators are used to control command execution in the terminal.

## && (AND operator)
Runs the second command only if the first succeeds.

Example:
mkdir test && cd test

## ; (Sequential operator)
Runs commands one after another regardless of success.

Example:
mkdir test; cd test

## || (OR operator)
Runs the second command only if the first fails.

Example:
cd fakefolder || echo "Folder does not exist"

## | (Pipe operator)
Passes output of one command to another.

Example:
ls -l | grep ".txt"

## > (Redirect output)
Saves output to a file (overwrites).

Example:
ls > files.txt

## >> (Append output)
Adds output to a file.

Example:
echo "hello" >> file.txt
