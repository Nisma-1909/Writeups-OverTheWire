# Bandit Level 1 → Level 2

## Challenge

In this level, the password for the next level is stored in a file named `-`.

I logged into the Bandit server as `bandit1` using the password I found in the previous level.

## Step 1 — Checking the files

After logging in, I wanted to see what was present in the current directory, so I ran:

```bash
ls
```

The output was:

```text
-
```

The file was literally named `-`.

## Step 2 — Trying to read the file

At first, the filename looked a little unusual because `-` is also used by many Linux commands for special options or standard input.

So instead of simply doing:

```bash
cat -
```

I used:

```bash
cat ./-
```

Here, `./` tells the shell that `-` refers to a file in the current directory.

## Step 3 — Getting the password

After running:

```bash
cat ./-
```

I got:

```text
Pk8fYLZg2hnHSz83plB1iEPKdD3QToB
```

This was the password for the next level, `bandit2`.

## Step 4 — Exiting

Once I had the password, I exited the Bandit server using:

```bash
exit
```

The connection was closed:

```text
logout
Connection to bandit.labs.overthewire.org closed.
```

## Password

The password I obtained for `bandit2` was:

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

The main thing I learned from this level was that filenames can sometimes look like command-line options.

Since the file was named `-`, using:

```bash
cat ./-
```

made it clear that I wanted to read the file named `-` in the current directory.

This was also a good reminder to pay attention to unusual filenames instead of assuming every file can be handled in the usual way.

## Result

**Bandit Level 1 → Level 2 completed ✅**
