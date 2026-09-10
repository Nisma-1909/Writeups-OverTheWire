# Bandit Level 11 → Level 12

## Challenge

The password is encoded using ROT13.

## Solution

I connected to Level 11:

`ssh bandit11@bandit.labs.overthewire.org -p 2220`

My first password attempt failed:

`Permission denied, please try again.`

I entered it again and logged in successfully.

I used `tr` to decode the ROT13 text:

`cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`

Output:

`The password is xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

Then I exited:

`exit`

## Commands Used

`ssh bandit11@bandit.labs.overthewire.org -p 2220`  
`cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`  
`exit`

## What I Learned

- ROT13 shifts every letter by 13 positions.
- `tr` can be used to replace characters.
- My first login attempt failed because I entered the password incorrectly.

## Result

Bandit Level 11 → Level 12 completed.
