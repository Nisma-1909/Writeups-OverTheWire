# Bandit Level 03 → Level 04

## Challenge

Find the hidden file containing the password.

## Solution

I checked the directory:

`ls`

Output:

`inhere`

I entered the directory:

`cd inhere`

Then I checked for hidden files:

`ls -a`

Output:

`.  ..  ...Hiding-From-You`

I found the hidden file `...Hiding-From-You`.

I read it:

`cat ...Hiding-From-You`

Output:

`xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

Then I exited:

`exit`

## Commands Used

`ls`  
`cd inhere`  
`ls -a`  
`cat ...Hiding-From-You`  
`exit`

## What I Learned

- `ls -a` shows hidden files.
- Files starting with `.` are hidden in Linux.

## Result

Bandit Level 3 → Level 4 completed.
