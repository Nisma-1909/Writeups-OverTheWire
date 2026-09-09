# Bandit Level 0 → Level 1

## 🎯 Objective

The goal of this level is to log in to the Bandit server using SSH and find the password for the next level.

## 🔐 Connecting to the Server

The challenge provides the following connection details:

- **Host:** `bandit.labs.overthewire.org`
- **Port:** `2220`
- **Username:** `bandit0`

I connected using:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
