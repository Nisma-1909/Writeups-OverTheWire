# Bandit Level 07 → Level 08

## Challenge

The password is stored in `data.txt` next to the word `millionth`.

## Solution

I checked the files:

`ls`

Output:

`data.txt`

I searched for `millionth` using `grep`:

`cat data.txt | grep "millionth"`

Output:

`millionth       xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

Then I exited:

`exit`

## Commands Used

`ls`  
`cat data.txt | grep "millionth"`  
`exit`

## What I Learned

- `grep` searches for specific text.
- The pipe `|` sends the output of one command to another command.

## Result

Bandit Level 7 → Level 8 completed.
