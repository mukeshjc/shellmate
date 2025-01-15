# 🛠️ shellmate

Your friendly shell companion that supercharges developer productivity with carefully crafted aliases and functions! 🚀

## 📥 Quick Install

```bash
curl -o ~/shelpers https://raw.githubusercontent.com/mukeshjc/shellmate/main/shelpers && echo "source ~/shelpers" >> ~/.$(basename $SHELL)rc && source ~/.$(basename $SHELL)rc
```

## 🎯 Features

### Aliases

#### `csvtojson`
Converts CSV data to JSON format
```bash
echo "name,age\njohn,25" | csvtojson
# Output: [{"name":"john","age":"25"}]
```

#### `files-intersection`
Find common lines between two files
```bash
files-intersection <(sort users1.txt) <(sort users2.txt)
# Output: Lines that exist in both files
```

#### `files-difference`
Find lines that are in first file but not in second
```bash
files-difference <(sort users1.txt) <(sort users2.txt)
# Output: Lines unique to users1.txt
```

### Functions

#### `scpfrom` 
Securely copy files (recursively if the source is a directory) from your EC2 dev machine to local
```bash
scpfrom /remote/path/file.txt /local/path/
# Copies file.txt from EC2 to local path
```

#### `scpto`
Securely copy files (recursively if the source is a directory) from local to your EC2 dev machine
```bash
scpto /local/path/file.txt /remote/path/
# Copies file.txt from local to EC2
```

#### `sync`
One-time directory sync between local and EC2 using rsync
```bash
sync /local/project/dir /remote/project/dir
# Syncs local directory to EC2
```

#### `contsync`
Continuous background sync of development directories to EC2 (runs every 5 seconds)
```bash
contsync &
# Starts background sync process
```

## 💡 Pro Tips
- Run `contsync &` when you want to work locally but keep your EC2 environment in sync
- The sync interval can be adjusted by modifying the `sleep` value in the `contsync` function
- Make sure your EC2_DEV_MACHINE_IP environment variable is set before using the sync functions

## 🔧 Requirements
- SSH key at `~/cloud-dev-server.pem`
- `EC2_DEV_MACHINE_IP` environment variable set
- `jq` installed for csvtojson alias
- `rsync` installed for sync functions

## 🤝 Contributing
Feel free to add your own productivity boosters! PRs welcome! 🎉
