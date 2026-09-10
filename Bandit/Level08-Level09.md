
# Bandit Level 08 → Level 09

## Challenge

Find the only line in `data.txt` that occurs once.

## Solution

I checked the file:

`ls`

Output:

`data.txt`

I sorted the lines and then used `uniq -u` to find the line that appears only once:

`sort data.txt | uniq -u`

Output:

`xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

Then I exited:

`exit`

## Commands Used

`ls`  
`sort data.txt | uniq -u`  
`exit`

## What I Learned

- `sort` sorts the lines.
- `uniq -u` shows only unique lines.
- `|` passes the output of one command to another.

## Result

Bandit Level 8 → Level 9 completed.
