# Bandit Level 7 → Level 8

## Challenge

In this level, the password for the next level is stored in a file called `data.txt`.

The password is on the same line as the word:

```text
millionth
```

So I needed to search through `data.txt` and find the line containing that word.

## Step 1 — Checking the file

I was already in the home directory after logging in as `bandit7`.

The file I needed was:

```text
data.txt
```

Instead of opening the whole file, I used `grep` to search specifically for the word `millionth`.

I ran:

```bash
cat data.txt | grep "millionth"
```

## Step 2 — Finding the password

The command returned:

```text
millionth       VR1ljMayciFxbnUokuQmJFw6QC9VKtub
```

The word `millionth` was followed by the password:

```text
VR1ljMayciFxbnUokuQmJFw6QC9VKtub
```

So this was the password for the next level, `bandit8`.

## Step 3 — Exiting

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
VR1ljMayciFxbnUokuQmJFw6QC9VKtub
```

## Commands Used

```bash
cat data.txt | grep "millionth"
exit
```

## What I Learned

This level introduced me to `grep`.

`grep` is useful when I need to search for specific text inside a file.

In this case:

```bash
grep "millionth" data.txt
```

would also work.

I used:

```bash
cat data.txt | grep "millionth"
```

which first displays the contents of `data.txt` and then passes the output to `grep` to search for `millionth`.

This is much easier than manually going through a large file looking for one particular word.

## Result

**Bandit Level 7 → Level 8 completed ✅**
