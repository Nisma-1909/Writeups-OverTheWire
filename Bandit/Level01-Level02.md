# Bandit Level 1 → Level 2

## Challenge

In this level, the password for the next level is stored in a file named `-`.

I logged into the server as `bandit1` using the password I got from the previous level.

## Step 1 — Checking the directory

First, I checked the files in the current directory:

```bash
ls
```

The output was:

```text
-
```

So the file was literally named `-`.

## Step 2 — Reading the file

Normally, I could use `cat filename` to read a file.

But here the filename is `-`.

The `-` character is usually interpreted by Linux commands as an option or as standard input, so I used `./` to clearly specify that it is a file in the current directory.

I ran:

```bash
cat ./-
```

This gave me:

```text
Pk8fYLZg2hnHSz83plB1iEPKdD3QToB
```

This was the password for the next level, `bandit2`.

## Step 3 — Exiting the server

After getting the password, I exited the Bandit server:

```bash
exit
```

The terminal showed:

```text
logout
Connection to bandit.labs.overthewire.org closed.
```

## Password

```text
Pk8fYLZg2hnHSz83plB1iEPKdD3QToB
```

## Commands Used

```bash
ls
cat ./-
exit
```

## What I Learned

- A Linux file can have a name such as `-`.
- `-` can have a special meaning when used with command-line programs.
- Using `./` tells Linux that the name refers to a file in the current directory.
- `cat ./-` can be used to read a file named `-`.

## Result

Successfully completed **Bandit Level 1 → Level 2** ✅
