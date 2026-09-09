# Bandit Level 0 → Level 1

## Challenge

This is the first level of Bandit. The main goal is to get access to the Bandit server and find the password needed for the next level.

The challenge gives the SSH login details:

- Username: `bandit0`
- Host: `bandit.labs.overthewire.org`
- Port: `2220`

## Step 1 — Connecting to the server

I used SSH with the given details:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
