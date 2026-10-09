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

cat << 'EOF' > reg
#!/usr/bin/env bash

if [ -z "$1" ]; then
    echo "Использование: $0 <имя_файла>"
    exit 1
fi

chmod +x "$1"
sudo cp "$1" /usr/local/bin/
EOF

chmod +x reg

./reg banner

6 TASK

cat << 'EOF' > check_comments.sh
#!/usr/bin/env bash

for file in *; do
    [ -f "$file" ] || continue

    first_line=$(head -n 1 "$file")
    case "$file" in
        *.c|*.js)
            if [[ "$first_line" =~ ^[[:space:]]*(\/\/|\/\*) ]]; then
                echo "$file: комментарий найден"
            fi
            ;;
        *.py)
            if [[ "$first_line" =~ ^[[:space:]]*# ]]; then
                echo "$file: комментарий найден"
            fi
            ;;
    esac
done
EOF

chmod +x check_comments.sh
./check_comments.sh

7 TASK

cat << 'EOF' > find_duplicates.sh
#!/usr/bin/env bash

target_dir="${1:-.}"

find "$target_dir" -type f -exec md5sum {} + | sort | uniq -w32 -dD
EOF

chmod +x find_duplicates.sh

8 TASK

cat << 'EOF' > archive_by_ext.sh
#!/usr/bin/env bash

dir="$1"
ext="$2"

if [ -z "$dir" ] || [ -z "$ext" ]; then
    echo "Использование: $0 <директория> <расширение>"
    exit 1
fi

find "$dir" -maxdepth 1 -type f -name "*.$ext" -print0 | tar --null -cvf "archive_${ext}.tar" -T -
EOF

chmod +x archive_by_ext.sh

9 TASK

cat << 'EOF' > spaces_to_tabs.sh
#!/usr/bin/env bash

input="$1"
output="$2"

if [ -z "$input" ] || [ -z "$output" ]; then
    echo "Использование: $0 <входной_файл> <выходной_файл>"
    exit 1
fi

sed 's/    /\t/g' "$input" > "$output"
EOF

chmod +x spaces_to_tabs.sh

10 TASK

cat << 'EOF' > find_empty_text.sh
#!/usr/bin/env bash

dir="${1:-.}"

find "$dir" -type f -empty -name "*.txt"
EOF

chmod +x find_empty_text.sh
