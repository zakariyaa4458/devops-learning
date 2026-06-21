 Level 15 – Boss Battle 3: Advanced Bash Scripting

## Task
1. Presents a menu to the user with the following options:

- Check disk space
- Show system uptime
- Backup the Arena directory and keep the last 3 backups
- Parse a configuration file settings.conf and display the values

2. Execute the chosen task.

## Overview
This project is an interactive Bash script that combines multiple Linux administration and scripting concepts into a single menu-driven application.

## Features
- Check disk space usage for the Arena directory.
- Display system uptime.
- Create timestamped backups of the Arena directory.
- Automatically retain only the latest 3 backups.
- Parse a configuration file (`settings.conf`) and display key-value pairs.

## Technologies & Commands Used
- Bash
- Functions
- Variables
- `case` statements
- `if` statements
- `while` loops
- `read`
- `df`
- `uptime`
- `tar`
- `date`
- `ls`
- `tail`
- `xargs`
- `IFS`

## Menu Options
1. Check disk space
2. Check system uptime
3. Backup the Arena directory and keep the last 3 backups
4. Parse `settings.conf` and display its values

## Learning Outcomes
This project demonstrates:
- Interactive menu creation
- Function-based scripting
- Backup automation
- File retention management
- Configuration file parsing
- Conditional logic and loops
- Combining multiple Bash concepts into a complete automation solution
