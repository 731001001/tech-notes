# tar

## How to archive files
```bash
tar -czvf archive.tar.gz file1 file2
```

## How to extract files
```bash
tar -xzvf archive.tar.gz
```

# scp

## How to copy files to remote server
```bash
scp file.txt user@server:/path
```

## How to copy files from remote server
```bash
scp user@server:/path/file.txt .
```

## How to copy directory to remote server
```bash
scp -r dir user@server:/path
```

## How to copy directory from remote server
```bash
scp -r user@server:/path/dir .
```