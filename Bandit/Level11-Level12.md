# Bandit Level 11 → Level 12

## Challenge

In this level, the password is stored in `data.txt`.

The contents of the file have been transformed using **ROT13**.

ROT13 is a simple substitution cipher where each letter is shifted 13 positions in the alphabet.

For example:

```text
A → N
B → O
C → P
...
N → A
```

So I needed to reverse the ROT13 transformation to get the original text and password.

## Step 1 — Connecting to the server

I connected as `bandit11` using SSH:

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

I entered the password from the previous level.

I initially entered it incorrectly and got:

```text
Permission denied, please try again.
```

After entering the correct password, I successfully logged in.

## Step 2 — Reading and decoding the file

The password was stored in `data.txt`.

I used `cat` to read the file and piped the output into `tr` to perform the ROT13 transformation:

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

The command returned:

```text
The password is GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
```

The text was successfully converted back from ROT13, revealing the password.

## Step 3 — Understanding the `tr` command

The important part of the command was:

```bash
tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

`tr` translates characters from one set to another.

The first set:

```text
A-Za-z
```

represents all uppercase and lowercase English letters.

The second set:

```text
N-ZA-Mn-za-m
```

maps each letter to the letter 13 positions away.

This effectively performs ROT13.

## Step 4 — Getting the password

The decoded output was:

```text
The password is GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
```

So the password for the next level, `bandit12`, was:

```text
GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
```

## Step 5 — Exiting

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
GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
```

## Commands Used

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
exit
```

## What I Learned

This level introduced me to **ROT13** and the Linux `tr` command.

ROT13 is a substitution cipher that shifts every letter by 13 positions. Since the alphabet has 26 letters, applying ROT13 again reverses the transformation.

I also learned how a Linux pipe can be used to pass the output of one command directly into another:

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Here, `cat` reads the file and `tr` transforms the characters.

## Result

**Bandit Level 11 → Level 12 completed ✅**
