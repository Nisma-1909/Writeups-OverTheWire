# Bandit Level 12 → Level 13

## Challenge

The password is inside a file that has been compressed and archived multiple times using different formats.

## Solution

I created a temporary directory:

`mktemp -d`

Output:

`/tmp/tmp.eMtvbnHthJ`

I copied the file into it:

`cp data.txt /tmp/tmp.eMtvbnHthJ`

Then I entered the directory:

`cd /tmp/tmp.eMtvbnHthJ`

The file was hex dumped, so I converted it back to binary:

`xxd -r data.txt > data`

I checked the file:

`file data`

It was gzip compressed.

So I renamed it:

`mv data data.gz`

Then decompressed it:

`gzip -d data.gz`

I checked it again:

`file data`

It was bzip2 compressed.

So I renamed it:

`mv data data.bz2`

Then decompressed it:

`bzip2 -d data.bz2`

I checked the result:

`file data`

It was gzip compressed again.

At one point I made a mistake:

`mv data data.bz2`

`gzip2 -d data.bz2`

I got:

`-bash: gzip2: command not found`

I then tried:

`gzip -d data.gz`

But got:

`gzip: data.gz: No such file or directory`

I exited and started the level again.

After starting again, I repeated the extraction:

`mktemp -d`

`cp data.txt /tmp/tmp.eMtvbnHthJ`

`cd /tmp/tmp.eMtvbnHthJ`

`xxd -r data.txt > data`

Then:

`file data`

`mv data data.gz`

`gzip -d data.gz`

The next file was bzip2:

`file data`

`mv data data.bz2`

`bzip2 -d data.bz2`

Then it was gzip again:

`file data`

`mv data data.gz`

`gzip -d data.gz`

This time `file` showed:

`data: POSIX tar archive`

I extracted it:

`tar -xf data`

Then checked the extracted file:

`file data5.bin`

Output:

`data5.bin: POSIX tar archive`

I extracted it:

`tar -xf data5.bin`

Then checked the next file:

`file data6.bin`

Output:

`data6.bin: bzip2 compressed data`

I made another mistake here:

`rm data`

`bzip2 -d data.bz2`

I got:

`bzip2: Can't open input file data.bz2: No such file or directory.`

I realized the file was actually named `data6.bin`.

So I renamed it:

`mv data6.bin data.bz2`

Then decompressed it:

`bzip2 -d data.bz2`

I checked the result:

`file data`

Output:

`data: POSIX tar archive`

I extracted it:

`tar -xf data`

Then checked the next file:

`file data8.bin`

Output:

`data8.bin: gzip compressed data`

I renamed it:

`mv data8.bin data.gz`

Then decompressed it:

`gzip -d data.gz`

I got an overwrite prompt:

`gzip: data already exists; do you wish to overwrite (y or n)?`

I entered:

`y`

Finally, I checked the file:

`file data`

Output:

`data: ASCII text`

I read it:

`cat data`

Output:

`The password is xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

## Commands Used

`mktemp -d`  
`cp data.txt /tmp/tmp.eMtvbnHthJ`  
`cd /tmp/tmp.eMtvbnHthJ`  
`xxd -r data.txt > data`  
`file data`  
`mv data data.gz`  
`gzip -d data.gz`  
`file data`  
`mv data data.bz2`  
`bzip2 -d data.bz2`  
`file data`  
`mv data data.gz`  
`gzip -d data.gz`  
`file data`  
`tar -xf data`  
`file data5.bin`  
`tar -xf data5.bin`  
`file data6.bin`  
`rm data`  
`bzip2 -d data.bz2`  
`mv data6.bin data.bz2`  
`bzip2 -d data.bz2`  
`file data`  
`tar -xf data`  
`file data8.bin`  
`mv data8.bin data.gz`  
`gzip -d data.gz`  
`y`  
`file data`  
`cat data`

## What I Learned

- `xxd -r` converts a hex dump back into binary.
- `file` is useful for identifying unknown file types.
- `gzip` is used for gzip compressed files.
- `bzip2` is used for bzip2 compressed files.
- `tar -xf` extracts tar archives.
- The filename does not always tell you the actual file format.
- Checking with `file` before choosing the decompression command is important.
- Small command or filename mistakes can stop the extraction.

## Result

Bandit Level 12 → Level 13 completed.
