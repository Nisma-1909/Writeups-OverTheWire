# Bandit Level 3 → Level 4

## Challenge

In this level, the password is stored in a hidden file inside the `inhere` directory.

I logged in as `bandit3` using the password I got from the previous level.

## Step 1 — Checking the current directory

First, I used:

```bash
ls
```

The output was:

```text
inhere
```

So I found a directory called `inhere`.

## Step 2 — Entering the directory

I moved into the `inhere` directory:

```bash
cd inhere
```

My prompt changed to:

```text
bandit3@bandit:~/inhere$
```

This confirmed that I was now inside the `inhere` directory.

## Step 3 — Looking for hidden files

I used:

```bash
ls -a
```

The `-a` option is important here because it shows **all files**, including hidden files.

The output was:

```text
.  ..  ...Hiding-From-You
```

I noticed a file named:

```text
...Hiding-From-You
```

The filename starts with three dots, so it wasn't shown when I used the normal `ls` command.

## Step 4 — Reading the hidden file

I used `cat` followed by the exact filename:

```bash
cat ...Hiding-From-You
```

This gave me:

```text
xZT Xq1rDJQWVAzdv5Chq1TQytTwuAMq
```

The actual output from my terminal was:

```text
xZTXq1rDJQWVAzdv5Chq1TQytTwuAMq
```

This was the password for the next level, `bandit4`.

## Password

```text
xZTXq1rDJQWVAzdv5Chq1TQytTwuAMq
```

## Commands Used

```bash
ls
cd inhere
ls -a
cat ...Hiding-From-You
```

## What I Learned

The main thing I learned from this level was how to find hidden files in Linux.

Using:

```bash
ls
```

only showed the normal directory contents.

Using:

```bash
ls -a
```

showed the hidden files as well.

I also learned that a filename can start with multiple dots, and I need to use the exact filename when reading it.

## Result

**Bandit Level 3 → Level 4 completed ✅**
