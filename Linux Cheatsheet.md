# Linux Commands Cheatsheet
## File operations
### Create Diretory
```zsh
mkdir {directory}
```
### Copy file
```zsh
# Copy file to directory 
cp {file} {directory} 

# Copy file f to directory and rename to file1
cp {file} {directory/file1}
```
### Move file & Rename
```zsh
# Move file to directory 
mv {file} {directory} 

# Move file f to directory and rename to file1
mv {file} {directory/file1}

# Rename file1 to file2
mv {file1} {file2}
```
### Delete File
```zsh
# Remove file
rm {file}

# Remove directory
rmdir {directory}

# Force remove
rm -f {file}

# Recursively remove
rm -r {directory}
```
### Remote Copy File
```zsh
# Copy local_file to remote_path in user at remote_ip 
scp local_file user@remote_ip:remote_path
# -r Recursively
```

## Logging
### Search
```zsh
# Find all lines containing 'target' in the file
grep 'target' file
```
### Watch
```zsh
# Watch the last 100 lines of a changing log file
tail -f -n 100 file
```
