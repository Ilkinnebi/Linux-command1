# Variables in Linux

Variables store data in memory temporarily. They are widely used in scripting.

## Syntax
```bash
variable_name=value
```

## Examples
```bash
name=Ilkin
echo $name

year=2025
echo "Year is $year"
```

## Environment variable
```bash
export PATH=$PATH:/my/custom/path
```

## Remove a variable
```bash
unset variable_name
```

## Inside a script
```bash
#!/bin/bash
username="ilkin"
echo "Salam, $username!"
```
