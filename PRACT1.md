1 TASK:

labex:/etc/ $ grep -o '^[^:]*' passwd | sort

2 TASK:

labex:/etc/ $ awk '{print $2, $1}' protocols | sort -n -r | head -n 5

awk '{print $2, $1}' protocols — читает файл protocols и меняет местами столбцы: первым печатает номер протокола ($2), вторым — его название ($1).

3 TASK:

