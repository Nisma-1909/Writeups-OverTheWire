
# Bandit Level 14 → Level 15

## Challenge

The password for Level 15 is the password for Level 14 sent to a service running on port `30000` on localhost.

## Solution

First I connected to Bandit Level 14:

`ssh bandit14@bandit.labs.overthewire.org -p 2220`

I used `nc` to connect to the service running on port `30000`:

`nc localhost 30000`

I entered the password from Level 14:

`xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

The server responded:

`Correct!`

Then it gave me the password for Level 15:

`xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

## Commands Used

`ssh bandit14@bandit.labs.overthewire.org -p 2220`

`nc localhost 30000`

## What I Learned

- `nc` (Netcat) can be used to connect to network services.
- `localhost` means the service is running on the same machine.
- Port `30000` is the port used by this Bandit challenge.
- The current level password can be sent to the service to get the next password.

## Result

Bandit Level 14 → Level 15 completed.
