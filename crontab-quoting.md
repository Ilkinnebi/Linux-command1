# Crontab and Quoting in Bash

## ⏰ Crontab - Scheduled Tasks in Linux

Crontab is used to schedule commands to run automatically at specific times and intervals.

### View current user’s crontab
```bash
crontab -l
```

### Edit crontab
```bash
crontab -e
```

### Remove crontab
```bash
crontab -r
```

### Crontab format
```
* * * * * command_to_run
- - - - -
| | | | |
| | | | +----- day of the week (0 - 6) (Sunday=0)
| | | +------- month (1 - 12)
| | +--------- day of month (1 - 31)
| +----------- hour (0 - 23)
+------------- minute (0 - 59)
```

### Common examples
```bash
*/5 * * * * /path/to/script.sh        # Run every 5 minutes
0 0 * * * /path/to/backup.sh          # Run every day at midnight
0 9 * * 1 /path/to/monday-task.sh     # Run every Monday at 9 AM
@reboot /path/to/boot-script.sh       # Run at system boot
```

---

## 📝 Bash Quoting: "", '', ``, ||, &&, ::

Quoting is used to control how strings and variables are interpreted in bash.

### Double quotes `"..."`

- Variables are expanded
- Command substitution works

```bash
name="Ilkin"
echo "Hello $name"    # Output: Hello Ilkin
```

### Single quotes `'...'`

- Everything is taken literally
- No variable or command substitution

```bash
echo 'Hello $name'    # Output: Hello $name
```

### Backticks `` `...` `` (Command substitution)

```bash
echo "Today is `date`"
```

🟡 **Note**: Prefer `$(...)` syntax over backticks:
```bash
echo "Today is $(date)"
```

---

## ⚙️ Operators

### `&&` – AND operator
Runs second command only if the first succeeds.

```bash
mkdir test && cd test
```

### `||` – OR operator
Runs second command only if the first fails.

```bash
mkdir test || echo "Failed"
```

### `::` – Not a standard Bash operator
In bash, `::` has no special meaning. Often used in programming languages like C++ or documentation formatting.

---

## ✅ Summary

| Syntax      | Purpose                                 |
|-------------|------------------------------------------|
| `"..."`     | Expands variables and commands           |
| `'...'`     | No expansion, literal text               |
| `` `...` `` | Command substitution (use `$(...)`)      |
| `&&`        | Run if previous succeeds                 |
| `||`        | Run if previous fails                    |
| `::`        | Not used in Bash (ignore or comment use) |
