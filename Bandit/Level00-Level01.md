# Bandit Level 0 → Level 1

## Challenge

The first level is about connecting to the OverTheWire Bandit server using SSH and finding the password for the next level.

The details given for the connection were:

- Username: `bandit0`
- Host: `bandit.labs.overthewire.org`
- Port: `2220`

## Step 1 — Connecting to the server

I connected using SSH:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

After entering the given password, I successfully logged in and got:

```text
bandit0@bandit:~$
```

## Step 2 — Checking the directory

I first used `ls` to see what files were available:

```bash
ls
```

The output was:

```text
readme
```

So there was a file called `readme`.

## Step 3 — Reading the file

I used the `cat` command to read the contents of the file:

```bash
cat readme
```

I got this output:

```text
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: 6y2kwnwK6rgrvvvpLaa2T1cpFEKOhNR
```

The password shown at the end is the password for the next level, `bandit1`.

## Password

```text
6y2kwnwK6rgrvvvpLaa2T1cpFEKOhNR
```

## Commands Used

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
```

## What I Learned

- How to connect to a remote Linux machine using SSH
- How to connect to a specific port
- How to use `ls` to see files in a directory
- How to use `cat` to read a file
- How to find information stored inside a file

## Result

Successfully completed **Bandit Level 0 → Level 1** ✅
