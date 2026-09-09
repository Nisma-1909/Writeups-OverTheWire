# Bandit Level 5 → Level 6

## Challenge

In this level, the password is stored somewhere inside the `inhere` directory.

There are a lot of files and directories, so instead of checking every file manually, I needed to find the file based on its properties.

The file I was looking for was:

- Exactly **1033 bytes** in size
- **Not executable**

## Step 1 — Entering the directory

After logging in as `bandit5`, I checked the current directory:

```bash
ls
```

The output showed:

```text
inhere
```

So I entered it:

```bash
cd inhere
```

Then I listed the contents:

```bash
ls
```

There were many directories:

```text
maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
```

There were too many files to check manually, so I decided to use `find`.

## Step 2 — Finding the correct file

I first tried:

```bash
find . -type f -size 1033c ! executable
```

But I got an error:

```text
find: paths must precede expression: `executable'
```

So the command syntax was wrong.

I corrected it by adding `-` before `executable`:

```bash
find . -type f -size 1033c ! -executable
```

This time, it worked and returned:

```text
./maybehere07/.file2
```

This meant that `.file2` inside `maybehere07` matched the conditions.

## Step 3 — Reading the file

I used `cat` with the path returned by `find`:

```bash
cat ./maybehere07/.file2
```

The output was:

```text
pXa26xhMWaC2SvDotA4r9EgZkuIOeSBW
```

This was the password for the next level, `bandit6`.

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

```text
pXa26xhMWaC2SvDotA4r9EgZkuIOeSBW
```

## Commands Used

```bash
ls
cd inhere
ls
find . -type f -size 1033c ! -executable
cat ./maybehere07/.file2
exit
```

## What I Learned

This level introduced the `find` command in a more useful way.

I used:

```bash
find . -type f -size 1033c ! -executable
```

Here:

- `.` means to search from the current directory
- `-type f` searches for regular files
- `-size 1033c` searches for files exactly 1033 bytes in size
- `! -executable` excludes executable files

I also learned that small syntax mistakes in Linux commands can give errors, and fixing the command based on the error is an important part of troubleshooting.

## Result

**Bandit Level 5 → Level 6 completed ✅**
