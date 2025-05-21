# Bash Scripting in Linux

## 📝 Basic Structure
```bash
#!/bin/bash
# This is a comment
echo "Hello, world!"
```

## 📦 Variables
```bash
name="Ilkin"
echo "My name is $name"
```

## 🔁 Conditional Statements
```bash
if [ $name == "Ilkin" ]; then
  echo "Welcome, Ilkin"
else
  echo "User not recognized"
fi
```

## 🔄 Loops

### For loop
```bash
for i in {1..5}; do
  echo "Number $i"
done
```

### While loop
```bash
counter=1
while [ $counter -le 3 ]; do
  echo "Counter $counter"
  ((counter++))
done
```

## ⚙️ Functions
```bash
say_hello() {
  echo "Hello $1"
}
say_hello "Ilkin"
```

## 🧪 Check if a file exists
```bash
if [ -f /etc/passwd ]; then
  echo "File exists"
fi
```

## 🔒 Make script executable
```bash
chmod +x script.sh
```

## 🧰 Practical Examples

### 1. Simple Backup Script
```bash
#!/bin/bash
tar -czvf backup_$(date +%F).tar.gz /home/ilkin
```

### 2. Check if user exists
```bash
#!/bin/bash
if id "$1" &>/dev/null; then
  echo "User $1 exists."
else
  echo "User $1 does not exist."
fi
```

### 3. Loop through files
```bash
for file in *.txt; do
  echo "Processing $file"
done
```
