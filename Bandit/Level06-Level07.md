# Bandit Level 06 → Level 07

## Challenge

Find the file that belongs to user `bandit7`, belongs to group `bandit6`, and has a size of 33 bytes.

## Solution

I connected to Level 6:

`ssh bandit6@bandit.labs.overthewire.org -p 2220`

I searched the whole filesystem:

`find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`

Output:

`/var/lib/dpkg/info/bandit7.password`

I read the file:

`cat /var/lib/dpkg/info/bandit7.password`

Output:

`xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

Then I exited:

`exit`

## Commands Used

`ssh bandit6@bandit.labs.overthewire.org -p 2220`  
`find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`  
`cat /var/lib/dpkg/info/bandit7.password`  
`exit`

## What I Learned

- `find /` searches from the root directory.
- `-user` searches by file owner.
- `-group` searches by group owner.
- `-size 33c` searches for exactly 33 bytes.
- `2>/dev/null` hides error messages.

## Result

Bandit Level 6 → Level 7 completed.
