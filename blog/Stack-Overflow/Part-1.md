# Stack 0verflow

### AIM:
To print the secret.

### Example:

<script src="https://gist.github.com/n41n4/496691de46d5202aec5585a722763ffa.js?file=snippet.c"></script>

### Stack

```
+--------------------+
| FUNCTION ARGUMENTS |
+====================+
| RETURN (RET)       |
+--------------------+
| SECRET[]           |
+--------------------+
| KEY[128]           |
+--------------------+ 
```

### Analysis
Execution flow of above example
1. A secret variable is created with some secret value.
2. Then a buffer is initialized with 128 bytes.
3. User input will be stored in buffer variable using `read` function.
4. Finally User input will be echoed back with welcome using printf.


```bash
┌─[inc0gn1t0@inc0gn1t0-VirtualBox]─[~/Stack0verflow]
└──╼ $./snippet 
Guest
Welcome Guest
```

### Exploit:

Enter any random string of len 128.

```bash

┌─[inc0gn1t0@inc0gn1t0-VirtualBox]─[~/Stack0verflow]
└──╼ $echo "AAAAAAAAAAAAAAAA...........AAAAAAAAA" | ./snippet
Welcome AAAAAAAAAAAAAAAA...........AAAAAAAAASup3r_S3cr37_S7r1n6

```

### Explanation
Here the culprit is `read` function.In this context `read` is used to take input from user.
So basically,`*read will not add null at the end of the string*` like scanf does.



### Practice
- [Task](Practice-1.html)
