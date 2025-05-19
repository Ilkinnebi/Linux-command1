# Alias in Linux

Alias allows you to create shortcuts for long commands.

## Syntax
```bash
alias name='command'
```

## Examples
```bash
alias ll='ls -l'
alias la='ls -la'
alias gs='git status'
alias update='sudo apt update && sudo apt upgrade -y'
```

## View all aliases
```bash
alias
```

## Remove an alias
```bash
unalias ll
```

## Make alias permanent
Edit your ~/.bashrc or ~/.bash_profile and add:
```bash
alias gs='git status'
```
Then run:
```bash
source ~/.bashrc
```
