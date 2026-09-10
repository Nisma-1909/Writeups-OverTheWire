# Bandit Level 10 → Level 11

## Challenge

The password is stored in a Base64 encoded file.

## Solution

I checked the files:

`ls`

Output:

`data.txt`

I checked the file type:

`file data.txt`

Output:

`data.txt: ASCII text`

I decoded the file using Base64:

`base64 -d data.txt`

Output:

`The password is xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

Then I exited:

`exit`

## Commands Used

`ls`  
`file data.txt`  
`base64 -d data.txt`  
`exit`

## What I Learned

- `base64 -d` decodes Base64 data.
- `file` can be used to check the type of a file.

## Result

Bandit Level 10 → Level 11 completed.
