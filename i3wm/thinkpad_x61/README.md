# Debian Setup

This repository contains the packages and configuration needed to reproduce my Debian environment.

## Install packages

```bash
sudo apt update
xargs -a packages.txt sudo apt install -y
