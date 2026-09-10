# Bandit Level 04 → Level 05

## Challenge

Find the password inside one of the files in `inhere`.

## Solution

I checked the directory:

`ls`

Output:

`inhere`

I entered it:

`cd inhere`

Then I listed the files:

`ls`

Output:

`-file00`  
`-file01`  
`-file02`  
`-file03`  
`-file04`  
`-file05`  
`-file06`  
`-file07`  
`-file08`  
`-file09`

The filenames started with `-`, so I used `--` before the filename:

`cat -- -file07`

Output:

`xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

Then I exited:

`exit`

## Commands Used

`ls`  
`cd inhere`  
`ls`  
`cat -- -file07`  
`exit`

## What I Learned

- `--` tells the command that the following text should be treated as a filename and not an option.
- This is useful when filenames start with `-`.

## Result

Bandit Level 4 → Level 5 completed.
