# Bandit Level 2 → Level 3

## Challenge

In this level, the password for the next level is stored in a file whose name contains spaces.

I logged in as `bandit2` using the password I obtained from the previous level.

## Step 1 — Checking the directory

First, I used `ls` to see what was inside the current directory:

```bash
ls
```

The output was:

```text
--spaces in this filename--
```

The filename contains spaces, so I knew I couldn't treat it like a normal filename without handling those spaces properly.

## Step 2 — Reading the file

I used `cat` and put the filename inside quotation marks:

```bash
cat "--spaces in this filename--"
```

Using quotes makes the shell treat the entire text as **one filename**, including the spaces.

## Step 3 — Getting the password

After running the command, I got:

```text
7ZZ2LFryKP2zEyvBl4m3cLcL7tGYJPME
```

This was the password for the next level, `bandit3`.

## Step 4 — Exiting

After getting the password, I exited the server:

```bash
exit
```

The connection was closed:

```text
logout
Connection to bandit.labs.overthewire.org closed.
```

## Password

The password I obtained for `bandit3` was:

```text
7ZZ2LFryKP2zEyvBl4m3cLcL7tGYJPME
```

## Commands Used

```bash
ls
cat "--spaces in this filename--"
exit
```

## What I Learned

The main thing I learned from this level was how to work with filenames containing spaces.

If a filename contains spaces, the shell normally treats each space-separated part as a separate argument. Putting the filename inside quotes makes the shell treat the complete filename as one argument.

For example:

```bash
cat "filename with spaces"
```

This is useful when working with files that have spaces or other characters that could confuse the shell.

## Result

**Bandit Level 2 → Level 3 completed ✅**
