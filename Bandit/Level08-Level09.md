# Bandit Level 8 → Level 9

## Challenge

In this level, the password is stored in `data.txt`.

The important clue is that the password is the **only line that occurs exactly once** in the file.

So instead of manually checking all the lines, I needed a way to:

1. Sort the lines
2. Find the line that appears only once

## Step 1 — Checking the file

After logging in as `bandit8`, I checked the current directory:

```bash
ls
```

The output was:

```text
data.txt
```

So `data.txt` was the file I needed to investigate.

## Step 2 — Sorting the file

I used the `sort` command together with `uniq`:

```bash
sort data.txt | uniq -u
```

### What does this command do?

First:

```bash
sort data.txt
```

sorts all the lines in `data.txt`.

Then the `|` symbol, called a **pipe**, sends the sorted output to the next command.

```bash
uniq -u
```

checks for unique lines and displays only the lines that occur exactly once.

The `-u` option means **unique**.

## Step 3 — Finding the password

The command returned:

```text
EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl
```

Since this was the only line that appeared exactly once, it was the password for the next level, `bandit9`.

## Step 4 — Exiting

After getting the password, I exited the server:

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
EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl
```

## Commands Used

```bash
ls
sort data.txt | uniq -u
exit
```

## What I Learned

This level taught me how to combine Linux commands using a **pipe (`|`)**.

The pipe allows the output of one command to become the input of another command.

For this level:

```bash
sort data.txt | uniq -u
```

`sort` arranged the lines so that identical lines were next to each other, which allowed `uniq` to identify the line that occurred only once.

I also learned that `uniq -u` is useful for finding lines that are unique within sorted input.

## Result

**Bandit Level 8 → Level 9 completed ✅**
