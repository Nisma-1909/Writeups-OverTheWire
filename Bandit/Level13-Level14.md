# Bandit Level 13 → Level 14

## Challenge

The password for Level 14 is not given directly.

Instead, there is a private SSH key called `sshkey.private` in the home directory. I need to use that key to log in as `bandit14`.

## Solution

First I connected to Bandit Level 13:

`ssh bandit13@bandit.labs.overthewire.org -p 2220`

After logging in, I checked the files:

`ls -la`

Output showed:

`sshkey.private`

So the private SSH key was available in the home directory.

I exited from the Bandit server:

`exit`

Then I tried to copy the private key to my Kali machine using `scp`:

`scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .`

It asked for the Bandit 13 password, so I entered it.

The file was copied to my Kali machine.

I first made a mistake while changing the permissions:

`chmod 400 ssh.privateky`

I got:

`chmod: cannot access 'ssh.privateky': No such file or directory`

I had typed the filename incorrectly.

The actual filename was `sshkey.private`, so I corrected it:

`chmod 400 sshkey.private`

Now I used the private key to connect to Level 14:

`ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220`

This logged me into `bandit14`.

I checked the directory:

`ls`

There was nothing useful in the home directory, so I went to the password directory.

I first made another mistake:

`cd /etc/b`

I got:

`-bash: cd: /etc/b: No such file or directory`

I corrected it:

`cd /etc/bandit_pass/`

Then I listed the files:

`ls`

There were password files for the different Bandit levels.

I specifically checked the `bandit14` file:

`ls bandit14`

Then I read it:

`cat bandit14`

Output:

`xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

This was the password for Level 15.

## Commands Used

`ssh bandit13@bandit.labs.overthewire.org -p 2220`

`ls -la`

`exit`

`scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .`

`chmod 400 ssh.privateky`

`chmod 400 sshkey.private`

`ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220`

`ls`

`cd /etc/b`

`cd /etc/bandit_pass/`

`ls`

`ls bandit14`

`cat bandit14`

## What I Learned

- `ssh` is used to connect to the Bandit server.
- `scp` can be used to copy files over SSH.
- `chmod 400` gives the private key the required permissions.
- `ssh -i` allows an SSH private key to be specified.
- The password files are stored inside `/etc/bandit_pass/`.
- I also learned that filenames and paths need to be typed correctly.

## Result

Bandit Level 13 → Level 14 completed.
