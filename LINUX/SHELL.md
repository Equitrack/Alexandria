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

```bash
KEY=value
ANOTHER_KEY="Some other value"
KEY_MULTI=value1:value2
```

- The variables are case-sensitive.
- Define variables using UPPER_CASE.
- Assigning multiple values using the colon : character.
- No space around the equals = symbol.
- There are two main categories, **environment variables** and **shell variables**.
- Environment variables are variables that are available **system-wide**.
- Shell variables are variables that apply only to the **current shell instance**.
