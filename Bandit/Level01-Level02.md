# Bandit Level 01 → Level 02

## Challenge

Find the password for Level 2.

## Solution

I logged in as `bandit1` and checked the directory:

`ls`

Output:

`-`

The filename was just `-`.

I used `./` before the filename so that it would be treated as a file in the current directory:

`cat ./-`

Output:

`xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

Then I exited:

`exit`

## Commands Used

`ls`  
`cat ./-`  
`exit`

## What I Learned

- `-` can have a special meaning in Linux commands.
- `./` can be used to specify a file in the current directory.

## Result

Bandit Level 1 → Level 2 completed.
