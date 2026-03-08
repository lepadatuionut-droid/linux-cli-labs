# Linux CLI Labs (Kali / Apporto) – Week 1

This repository contains my hands‑on Linux terminal practice performed in a Kali Linux (Apporto) environment.

## What’s included
- `week_1_Tutorial.zip` – exported artifact from the Kali VM (proof of work).
- **Week 1 highlights**: directory & file operations, recursive copy/delete, exporting command history, and packaging outputs for download.

## Reproduce key Week 1 steps
```bash
# Create lab folder and files
mkdir -p ~/Documents/command_line
cd ~/Documents/command_line

touch file1.txt file2.txt file3.txt
mkdir recursive recursive_test linux.lunches

# Move/copy examples
mv file1.txt recursive_test/
cp -r recursive ~/Desktop

# Export command history
history > my_history.txt

# Package to Desktop
cd ~/Desktop
zip -r week_1_Tutorial.zip ~/Documents/command_line
