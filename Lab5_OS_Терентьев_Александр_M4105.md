### Подготовка текстового файла

```bash
terentev@debian:~$ cat labwork5_text
In the silence of the night, I read.
No
I found a secret in the old book.
Me
Whether 'tis nobler in the the mind to suffer.
The air was abuzz with strange whispers.
It was the year 101 or perhaps 808.
Never never shall I return to that place.
Oh
A single light shone in the dark window.
The room number was 454 on that floor.
Life is is but a dream within a dream.
It was an abz mystery, truly absolute.
```

---

### Задание 1. Вывести строки из двух символов, не являющихся цифрами

```bash
terentev@debian:~$ grep -E '^[^0-9]{2}$' labwork5_text
No
Me
Oh
```

### Задание 2. Вывести слова из одной буквы и номера строк

```bash
terentev@debian:~$ grep -n -o -w '[a-zA-Z]' labwork5_text
1:I
3:I
3:a
8:I
10:A
12:a
12:a
```

### Задание 3. Вывести слова, начинающиеся на “ab” и заканчивающиеся на “z”

```bash
terentev@debian:~$ grep -o -E '\bab[a-zA-Z]*z\b' labwork5_text
abuzz
abz
```

### Задание 4. Вывести строки с трехзначным числом-палиндромом

```bash
terentev@debian:~$ grep -E '\b([0-9])[0-9]\1\b' labwork5_text
It was the year 101 or perhaps 808.
The room number was 454 on that floor.
```

### Задание 5. Вывести строки с двумя одинаковыми словами подряд

```bash
terentev@debian:~$ grep -i -E '\b([a-zA-Z]+)\s+\1\b' labwork5_text
Whether 'tis nobler in the the mind to suffer.
Never never shall I return to that place.
Life is is but a dream within a dream.
```

---
### Задание 6. Работа с системными файлами (.profile)

```bash
terentev@debian:~$ cat ~/.profile | grep -c '\.profile'
cat: /home/terentev/.profile: Нет такого файла или каталога
0
```
### Задание 7. Поиск команд с SUID-битом в /usr/bin

```bash
terentev@debian:~$ ls -l /usr/bin | grep '^...s'
-rwsr-xr-x 1 root root        62672 дек 14 17:00 chfn
-rwsr-xr-x 1 root root        52880 дек 14 17:00 chsh
-rwsr-xr-x 1 root root        88496 дек 14 17:00 gpasswd
-rwsr-xr-x 1 root root        59704 ноя 21  2024 mount
-rwsr-xr-x 1 root root        48896 дек 14 17:00 newgrp
-rwsr-xr-x 1 root root        68248 дек 14 17:00 passwd
-rwsr-sr-x 1 root mail       101664 мар  1  2022 procmail
-rwsr-xr-x 1 root root        72000 ноя 21  2024 su
-rwsr-xr-x 1 root root       281624 дек 30 23:07 sudo
-rwsr-xr-x 1 root root        35128 ноя 21  2024 umount
```

---
### Запись команд в файл commands

```bash
terentev@debian:~$ echo "grep -E '^[^0-9]{2}$' labwork5_text" > commands
terentev@debian:~$ echo "grep -n -o -w '[a-zA-Z]' labwork5_text" >> commands
terentev@debian:~$ echo "grep -o -E '\bab[a-zA-Z]*z\b' labwork5_text" >> commands
terentev@debian:~$ echo "grep -E '\b([0-9])[0-9]\1\b' labwork5_text" >> commands
terentev@debian:~$ echo "grep -i -E '\b([a-zA-Z]+)\s+\1\b' labwork5_text" >> commands
terentev@debian:~$ echo "cat ~/.profile | grep -c '\.profile'" >> commands
terentev@debian:~$ echo "ls -l /usr/bin | grep '^...s'" >> commands
```
### Итоговый файл с командами (commands)

```bash
terentev@debian:~$ cat commands
grep -E '^[^0-9]{2}$' labwork5_text
grep -n -o -w '[a-zA-Z]' labwork5_text
grep -o -E '\bab[a-zA-Z]*z\b' labwork5_text
grep -E '\b([0-9])[0-9]\1\b' labwork5_text
grep -i -E '\b([a-zA-Z]+)\s+\1\b' labwork5_text
cat ~/.profile | grep -c '\.profile'
ls -l /usr/bin | grep '^...s'
```