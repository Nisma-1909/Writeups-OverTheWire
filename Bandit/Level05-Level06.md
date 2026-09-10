# Bandit Level 05 → Level 06

## Challenge

Find the file that has the required size and is not executable.

## Solution

I checked the directory:

`ls`

Output:

`inhere`

I entered it:

`cd inhere`

There were many directories:

`ls`

Output:

`maybehere00`  
`maybehere01`  
`maybehere02`  
`...`  
`maybehere19`

Instead of checking each directory manually, I used `find`.

My first command was:

`find . -type f -size 1033c ! executable`

I got an error:

`find: paths must precede expression: 'executable'`

I corrected the command:

`find . -type f -size 1033c ! -executable`

Output:

`./maybehere07/.file2`

I read the file:

`cat ./maybehere07/.file2`

Output:

`xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

Then I exited:

`exit`

## Commands Used

`ls`  
`cd inhere`  
`ls`  
`find . -type f -size 1033c ! executable`  
`find . -type f -size 1033c ! -executable`  
`cat ./maybehere07/.file2`  
`exit`

## What I Learned

- `find` can search for files using different conditions.
- `-type f` searches for regular files.
- `-size 1033c` searches for a file with exactly 1033 bytes.
- `! -executable` finds files that are not executable.
- The error helped me fix the syntax of the command.

## Result

Bandit Level 5 → Level 6 completed.
