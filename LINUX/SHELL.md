The shell is an interpreter program.

**Types:**

- SH (Bourne Shell): Original and basic shell.
- BASH (Bourne Again Shell): Standard GNU shell.
- CSH (C Shell): It's similar to C lenguage.
- TSCH (TENEX C SHELL): Superset of the common C shell.
- KSH (Korn Shell): Used to AIX, HP-UX and Solaris.

> Some shells like bash or zsh support auto-completion.

**Bash startups files:**

Files read:

- /etc/profile
- ~/.bash_profile,
- ~/.bash_login or ~/.profile: first existing readable file is read
- ~/.bash_logout upon logout.

**Environment variables:**

- The variables are case-sensitive.
- Define variables using UPPER_CASE.
- Assigning multiple values using the colon : character.
- No space around the equals = symbol.

```bash
VARIABLE_UNO="1" 
```