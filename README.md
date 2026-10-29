# Linux File Permissions Lab 

## Goal 
Understand and test read, write, and execute permissions in Linux.

## Enviroment 
Ubntu on Windows using WSL.

## Tests and Results 
| Permissions | Test | Result |
|---|---|---|
| demo.txt: 400 | Read the file | Success |
| demo.txt: 400 | Append a line | Permission denied |
| demo.txt  600 | Append a line | Success |
| hello.sh: 600 | Run ./hello.sh | Permission denied |
| hello.sh: 700 | Run ./hello.sh | Lab works! |
## What I learned 
- Read ( r = 4 ): view a file's contrents. 
- Write ( w = 2 ): change a file's conennts.
- Execute (x = 1): run a file as a program.
- 600 give the owner read and write permission.
- 700 give the owner read, write , and execute permissions. 
- In both  casese , the group and others users have no permissions. 
## How to Repeat the Tests

Run these commands inside the project folder as a regular user.

### Read and write permissions

```bash
chmod 400 demo.txt
cat demo.txt
printf 'Test line\n' >> demo.txt
```

Reading should work. Appending should fail with "Permission denied".

```bash
chmod 600 demo.txt
printf 'Test line\n' >> demo.txt
cat demo.txt
```

Appending should now work.

### Execute permission

```bash
chmod 600 hello.sh
./hello.sh
```

Execution should fail with "Permission denied".

```bash
chmod 700 hello.sh
./hello.sh
```

Expected output: `Lab works!`

## Evidence

See `evidence/permissions.txt` for the final file permissions.

## Limitations

Tests were performed with one regular user account.
Access from a second user account was not tested.
Repeating the write test adds another line to demo.txt.
