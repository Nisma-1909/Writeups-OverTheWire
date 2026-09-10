# Bandit Level 00 → Level 01

## Challenge

Login to Bandit Level 0 and find the password for Level 1.

## Solution

I connected to the Bandit server using SSH:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

After logging in, I checked the files:

```bash
ls
```

Output:

```text
readme
```

I read the file:

```bash
cat readme
```

The password was displayed in the file.

```text
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

Then I exited:

```bash
exit
```

## Commands Used

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
exit
```

## What I Learned

- `ls` shows the files in the current directory.
- `cat` displays the contents of a file.
- SSH is used to connect to the Bandit server.

## Result

Bandit Level 0 → Level 1 completed.
