1 TASK:

labex:/etc/ $ grep -o '^[^:]*' passwd | sort

2 TASK:

labex:/etc/ $ awk '{print $2, $1}' protocols | sort -n -r | head -n 5

3 TASK:

text="$1"
len=${#text}

line=$(printf '%*s' "$((len + 2))" '' | tr ' ' '-')

printf "+%s+\n" "$line"
printf "| %s |\n" "$text"
printf "+%s+\n" "$line"

4 TASK:

grep -oE '[a-zA-Z_][a-zA-Z0-9_]*' hello.c | sort -u | tr '\n' ' ' && echo

5 TASK:
