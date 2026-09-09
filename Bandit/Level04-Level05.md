# Bandit Level 4 → Level 5

## Challenge

In this level, the password is stored in one of the files inside the `inhere` directory.

The tricky part is that the files have names starting with `-`.

## Step 1 — Checking the directory

After logging in as `bandit4`, I first checked the current directory:

```bash
ls
```

I got:

```text
inhere
```

So I entered the directory:

```bash
cd inhere
```

## Step 2 — Checking the files

Inside `inhere`, I ran:

```bash
ls
```

There were multiple files:

```text
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
```

I needed to find which one contained the password.

## Step 3 — Reading the file

I noticed that the filenames all started with `-`.

A `-` can have a special meaning in Linux commands, so I used `--` before the filename.

I ran:

```bash
cat -- -file07
```

The `--` tells the command that the options have ended, so `-file07` is treated as a filename instead of an option.

## Step 4 — Getting the password

The command returned:

```text
6C7h9GD8Mai5nr7wo1RonrzFjj9yIrG
```

This was the password for the next level, `bandit5`.

## Step 5 — Exiting

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

```text
6C7h9GD8Mai5nr7wo1RonrzFjj9yIrG
```

## Commands Used

```bash
ls
cd inhere
ls
cat -- -file07
exit
```

## What I Learned

This level taught me how to deal with filenames that start with `-`.

The `--` is useful because it tells the command that anything after it should be treated as an argument or filename, not as a command option.

So:

```bash
cat -- -file07
```

allows `cat` to correctly read the file named `-file07`.

## Result

**Bandit Level 4 → Level 5 completed ✅**
