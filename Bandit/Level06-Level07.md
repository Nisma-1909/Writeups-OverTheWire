# Bandit Level 6 → Level 7

## Challenge

In this level, the password is stored somewhere on the server.

The file has these properties:

- Owned by user `bandit7`
- Owned by group `bandit6`
- Exactly `33` bytes in size

Since I didn't know where the file was located, I had to search the whole filesystem.

## Step 1 — Connecting to the server

I connected as `bandit6` using SSH:

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

After entering the password from the previous level, I got into the server.

## Step 2 — Searching the filesystem

Since the file could be anywhere, I used `find` starting from `/`:

```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

The command returned:

```text
/var/lib/dpkg/info/bandit7.password
```

So this was the file matching all the required conditions.

### Breaking down the command

```bash
find /
```

Starts searching from the root directory, so the entire filesystem is searched.

```bash
-user bandit7
```

Finds files owned by the user `bandit7`.

```bash
-group bandit6
```

Finds files owned by the group `bandit6`.

```bash
-size 33c
```

Finds files that are exactly 33 bytes in size.

```bash
2>/dev/null
```

The search goes through many directories where I don't have permission to read. Instead of filling the terminal with permission-denied errors, `2>/dev/null` hides those error messages.

## Step 3 — Reading the file

Once I found the correct file, I used `cat` with its full path:

```bash
cat /var/lib/dpkg/info/bandit7.password
```

The output was:

```text
Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3
```

This was the password for the next level, `bandit7`.

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
Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3
```

## Commands Used

```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
exit
```

## What I Learned

This level taught me how to search for files based on their properties instead of their names.

I learned how to use `find` with:

- `-user` to search by file owner
- `-group` to search by group
- `-size` to search by file size
- `2>/dev/null` to hide permission errors

The most useful part was realizing that when the location of a file is unknown, I can start the search from `/` and use its known properties to narrow down the result.

## Result

**Bandit Level 6 → Level 7 completed ✅**
