# Bandit Level 9 → Level 10

## Challenge

In this level, the password is stored in `data.txt`.

The file contains a mixture of readable text and binary data, so simply using `cat` would produce a lot of unreadable output.

The clue was that the password is contained in one of the **human-readable strings**, and the relevant string contains several `=` characters.

## Step 1 — Checking the file

After logging in as `bandit9`, I checked the current directory:

```bash
ls
```

The output was:

```text
data.txt
```

So `data.txt` was the file I needed to examine.

## Step 2 — Extracting readable text

Since the file contains binary data, I used the `strings` command.

```bash
strings data.txt
```

`strings` extracts sequences of printable characters from a binary file.

However, there could be many readable strings, so I needed to narrow down the output.

## Step 3 — Searching for `=`

I piped the output of `strings` into `grep`:

```bash
strings data.txt | grep "="
```

This searches the readable strings for lines containing the `=` character.

The output included:

```text
========== the
[==p+
=zW}
========== password
Y========== is
k8c=
yo=-
=A@.
.=O],
=l"C"m
j=9$
========== B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
'=5G
```

The important line was:

```text
========== B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```

The password was:

```text
B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```

This was the password for the next level, `bandit10`.

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
B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```

## Commands Used

```bash
ls
strings data.txt | grep "="
exit
```

## What I Learned

This level taught me how to work with files that contain binary data.

The `strings` command is useful for extracting readable text from binary files.

I also used a pipe:

```bash
strings data.txt | grep "="
```

Here, `strings` extracts the readable text and `grep "="` filters that output to show only lines containing `=`.

This made it much easier to identify the line containing the password without having to manually inspect the entire file.

## Result

**Bandit Level 9 → Level 10 completed ✅**
