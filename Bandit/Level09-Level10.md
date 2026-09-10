# Bandit Level 09 → Level 10

## Challenge

Find the password in a file containing mostly non-readable data.

## Solution

I checked the files:

`ls`

Output:

`data.txt`

I used `strings` to extract readable text and then searched for `=`:

`strings data.txt | grep "="`

I got several results:

`========== the`  
`[==p+`  
`=zW}`  
`========== password`  
`Y========== is`  
`k8c=`  
`yo=-`  
`=A@.`  
`.=O],`  
`=l"C"m`  
`j=9$`  
`========== xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`  
`'=5G`

The useful line contained the password.

Then I exited:

`exit`

## Commands Used

`ls`  
`strings data.txt | grep "="`  
`exit`

## What I Learned

- `strings` extracts readable text from files.
- `grep` can filter the output for specific characters or words.
- Pipes are useful for combining commands.

## Result

Bandit Level 9 → Level 10 completed.
