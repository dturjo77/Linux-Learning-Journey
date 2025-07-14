

###🧠 What is grep?
Think of grep like a super-powered "find" tool that helps you look for words or sentences in files or computer messages (called output). Just like you use Ctrl+F to find something in a web page or document, grep helps you do that in the terminal (a computer’s text screen).

🧪 Basic Use:
🔹 grep "word" file.txt

This means: “Hey computer, look inside file.txt and show me the lines that have the word ‘word’ in them.”

# Some grep Magic Options:
| Option   | What It Does                                          | Like...                  |
|----------|-------------------------------------------------------|-------------------------------------------|
| `-i`     | Ignores if letters are big or small (A=a)             | "Word" = "word" = "WORD"                  |
| `-v`     | Opposite search: shows lines that don’t have the word | Like saying “Show everything except this” |
| `-n`     | Shows line numbers                                    | Like page numbers in books 📖             |
| `-l`     | Only tells you which files have the word              | Not the lines, just filenames             |
| `-r`     | Looks inside folders and all files inside them too    | Like opening all drawers in your room     |
| `-w`     | Finds only whole words                                | “cat” is cat, not “scatter” 🐱            |
| `--color`| Highlights the found word in color                    | Easier to spot! 🌈                        |

📘 Some Examples:

🔍 Search in a file:  grep "apple" fruits.txt   ➜ Looks for “apple” in the file called fruits.txt.

📂 Search in a folder:  ps aux | grep firefox    ➜ Looks for “error” in all the files inside that folder.

🚿 Search from another command:  ps aux | grep firefox   ➜ This says: “Show me the programs running, but only show the ones with ‘firefox’ in them.”
