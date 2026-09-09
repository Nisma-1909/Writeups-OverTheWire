# Bandit Level 10 → Level 11

## Challenge

In this level, the password is stored in `data.txt`, but it is encoded using Base64.

So the first thing I needed to figure out was what type of data was inside the file and then decode it.

## Step 1 — Connecting to the server

I connected as `bandit10` using SSH:

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

After entering the password from the previous level, I successfully logged in.

## Step 2 — Checking the directory

I used:

```bash
ls
```

The output was:

```text
data.txt
```

So `data.txt` was the file I needed to investigate.

## Step 3 — Checking the file type

I used the `file` command:

```bash
file data.txt
```

The output was:

```text
data.txt: ASCII text
```

This showed that the file contained normal text rather than binary data.

## Step 4 — Decoding the contents

The challenge involved Base64 encoding, so I used the `base64` command with the `-d` option.

```bash
base64 -d data.txt
```

The output was:

```text
The password is pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro
```

The password was:

```text
pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro
```

This was the password for the next level, `bandit11`.

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
pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro
```

## Commands Used

```bash
ls
file data.txt
base64 -d data.txt
exit
```

## What I Learned

This level introduced Base64 decoding.

Base64 is a way of representing binary data using printable characters. It is an **encoding**, not encryption, so it can be decoded when the correct encoding is known.

I used:

```bash
base64 -d data.txt
```

The `-d` option tells the `base64` command to decode the input.

The decoded output directly revealed the password.

## Result

**Bandit Level 10 → Level 11 completed ✅**
