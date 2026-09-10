# Bandit Level 12 → Level 13

## Challenge

This level was a little different from the previous ones.

The contents of `data.txt` were hexdumped, and the actual data had been compressed multiple times using different compression formats.

So the basic idea was:

1. Convert the hexdump back into binary data.
2. Check what type of file it is.
3. Rename it with the correct extension.
4. Decompress it.
5. Check the resulting file again.
6. Repeat until the actual text containing the password is found.

## Step 1 — Creating a temporary directory

The Bandit server doesn't allow normal write access to the home directory, so I created a temporary directory:

```bash
mktemp -d
```

I got:

```text
/tmp/tmp.wVzkQ4i0CQ
```

Then I copied `data.txt` into it:

```bash
cp data.txt /tmp/tmp.wVzkQ4i0CQ
```

and moved into the directory:

```bash
cd /tmp/tmp.wVzkQ4i0CQ
```

## Step 2 — Converting the hexdump back to binary

The `data.txt` file was a hexdump, so I used `xxd` to reverse it:

```bash
xxd -r data.txt > data
```

Then I checked the resulting file:

```bash
file data
```

The output was:

```text
data: gzip compressed data, was "data2.bin", last modified: Wed Jun 24 14:58:58 2026, max compression, from Unix, original size modulo 2^32 578
```

So the file was gzip compressed.

## Step 3 — Decompressing the gzip file

I renamed the file so that it had the appropriate `.gz` extension:

```bash
mv data data.gz
```

Then decompressed it:

```bash
gzip -d data.gz
```

I checked the result:

```bash
file data
```

This time I got:

```text
data: bzip2 compressed data, block size = 900k
```

So the next compression format was **bzip2**.

## Step 4 — Decompressing the bzip2 file

I renamed it:

```bash
mv data data.bz2
```

Then decompressed it:

```bash
bzip2 -d data.bz2
```

Checking the file again:

```bash
file data
```

gave:

```text
data: gzip compressed data, was "data4.bin", last modified: Wed Jun 24 14:58:58 2026, max compression, from Unix, original size modulo 2^32 20480
```

So I was back to gzip compression.

## Step 5 — A mistake

At this point, I accidentally renamed the file incorrectly:

```bash
mv data data.bz2
```

and then tried:

```bash
gzip2 -d data.bz2
```

The terminal returned:

```text
Command 'gzip2' not found, did you mean:
  command 'bzip2' from deb bzip2
  command 'gzip' from deb gzip
```

I realized I had typed `gzip2` instead of `gzip`.

I then tried:

```bash
gzip -d data.gz
```

but got:

```text
gzip: data.gz: No such file or directory
```

because the file wasn't actually named `data.gz` at that point.

I exited and started the level again.

## Step 6 — Starting again

After logging back in, I created another temporary directory:

```bash
mktemp -d
```

This time I got:

```text
/tmp/tmp.wVzkQ4i0CQ
```

I repeated the initial steps:

```bash
cp data.txt /tmp/tmp.wVzkQ4i0CQ
cd /tmp/tmp.wVzkQ4i0CQ
xxd -r data.txt > data
```

Then:

```bash
file data
```

showed:

```text
data: gzip compressed data, was "data2.bin", last modified: Wed Jun 24 14:58:58 2026, max compression, from Unix, original size modulo 2^32 578
```

I renamed and decompressed it:

```bash
mv data data.gz
gzip -d data.gz
```

Then:

```bash
file data
```

gave:

```text
data: bzip2 compressed data, block size = 900k
```

So I continued following the file type each time.

## Step 7 — Following the compression chain

I renamed and decompressed the bzip2 file:

```bash
mv data data.bz2
bzip2 -d data.bz2
```

Then checked it:

```bash
file data
```

Output:

```text
data: gzip compressed data, was "data4.bin", last modified: Wed Jun 24 14:58:58 2026, max compression, from Unix, original size modulo 2^32 20480
```

This time I correctly renamed it:

```bash
mv data data.gz
gzip -d data.gz
```

Then:

```bash
file data
```

gave:

```text
data: POSIX tar archive (GNU)
```

So now the file was a TAR archive.

## Step 8 — Extracting the TAR archive

I extracted it using:

```bash
tar -xf data
```

Then checked the new file:

```bash
file data5.bin
```

Output:

```text
data5.bin: POSIX tar archive (GNU)
```

So there was another TAR archive inside.

I extracted that as well:

```bash
tar -xf data5.bin
```

Then checked the next file:

```bash
file data6.bin
```

The output was:

```text
data6.bin: bzip2 compressed data, block size = 900k
```

So the compression chain continued.

## Step 9 — Decompressing again

I tried:

```bash
rm data
bzip2 -d data.bz2
```

but got:

```text
bzip2: Can't open input file data.bz2: No such file or directory.
```

I realized the bzip2 file was actually named `data6.bin`.

So I renamed it:

```bash
mv data6.bin data.bz2
```

Then decompressed it:

```bash
bzip2 -d data.bz2
```

Checking the result:

```bash
file data
```

gave:

```text
data: POSIX tar archive (GNU)
```

I extracted it:

```bash
tar -xf data
```

Then checked the next file:

```bash
file data8.bin
```

The output was:

```text
data8.bin: gzip compressed data, was "data9.bin", last modified: Wed Jun 24 14:58:58 2026, max compression, from Unix, original size modulo 2^32 49
```

## Step 10 — Final decompression

I renamed the gzip file:

```bash
mv data8.bin data.gz
```

and decompressed it:

```bash
gzip -d data.gz
```

I got a prompt asking whether to overwrite an existing file:

```text
gzip: data already exists; do you wish to overwrite (y or n)?
```

I entered:

```text
y
```

Then checked the file:

```bash
file data
```

Finally, the output was:

```text
data: ASCII text
```

That meant I had finally reached normal readable text.

## Step 11 — Getting the password

I used:

```bash
cat data
```

The output was:

```text
The password is [HIDDEN]
```

The password for the next level is hidden below.

<details>
<summary>🔐 Reveal password</summary>

```text
qQYQiHOBPR8zR61qxYqX45quvihF2uzk
```

</details>

## Commands Used

```bash
mktemp -d
cp data.txt /tmp/tmp.wVzkQ4i0CQ
cd /tmp/tmp.wVzkQ4i0CQ
xxd -r data.txt > data
file data
mv data data.gz
gzip -d data.gz
mv data data.bz2
bzip2 -d data.bz2
mv data data.gz
gzip -d data.gz
tar -xf data
file data5.bin
tar -xf data5.bin
file data6.bin
mv data6.bin data.bz2
bzip2 -d data.bz2
tar -xf data
file data8.bin
mv data8.bin data.gz
gzip -d data.gz
file data
cat data
```

## What I Learned

This level taught me how to identify and handle different types of compressed files.

The most important command was:

```bash
file data
```

Instead of guessing what compression format I was dealing with, I checked the file type after every step.

The general process was:

```text
hexdump
   ↓
xxd -r
   ↓
gzip
   ↓
bzip2
   ↓
gzip
   ↓
tar
   ↓
tar
   ↓
bzip2
   ↓
tar
   ↓
gzip
   ↓
ASCII text
```

## Result

**Bandit Level 12 → Level 13 completed ✅**
