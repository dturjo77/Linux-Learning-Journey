

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


###🗣️ `echo` — Like Talking to the Computer

Imagine you want your computer to say something on the screen.

✨ `echo` does that!  
It just **prints** whatever you tell it.

echo Hello!
👶 Computer says:  
Hello!

📦 Some `echo` Tricks:

| Option | What it Does | Like... |
|--------|---------------|---------|
| `-n`   | Don’t go to the next line | Like saying something without pressing "Enter" 🛑↩️ |
| `-e`   | Understand special things like `\n` (new line), `\t` (tab) | Magic codes for new lines or spaces 🎩 |
| `-E`   | Turn off that magic (default) | Just show it as normal text 🙃 |

💡 Example:

echo -e "Hello\nWorld"


### ✂️ `sed` — Like a Magic Text Editor Robot

Now imagine you have a notebook full of words, and you want to:

- Fix a spelling mistake  
- Erase a sentence  
- Add a line  
- Change something

👉 `sed` does all that to **text files or lines**.  
It’s like a **robot editor** that finds and fixes stuff! 🤖

🪄 Most Common Trick: Replace Words

sed 's/cat/dog/' file.txt
Means:  
> “Hey, in each line of `file.txt`, find the **first** word ‘cat’ and change it to ‘dog’.”

To change **all cats** in the line:
sed 's/cat/dog/g'

`g` = **global** = everywhere in the line 🌍

🧹 More `sed` Superpowers:

| Command  | What it Does               | Like...                        |
|----------|----------------------------|--------------------------------|
| `d`      | Delete a line              | Trash it! 🗑️                   |
| `p`      | Print matching lines       | Show me those! 🕵️             |
| `i\text` | Insert text before a line  | Sneak it in before ✍️          |
| `a\text` | Add text after a line      | Add after 📌                   |
| `c\text` | Change the whole line      | Rewrite it completely 📝       |

🛠️ `sed` Options:

| Option | What it Means                            | Like...               |
|--------|-------------------------------------------|------------------------|
| `-i`   | Edit the file for real (save changes)     | Edit forever 😮        |
| `-n`   | Be quiet unless I say "print"             | Silent mode 🤫         |
| `-e`   | Do more than one command at once          | Multi-tasking 🤹       |
| `-r`   | Use advanced search patterns (some systems) | Power mode 💥        |

🧪 Examples

🔈 **Just say something:**
echo "I love ice cream"

🐈 **Turn all cats into dogs in a file:**
sed 's/cat/dog/g' animals.txt

🧽 **Replace and save it:**
sed -i 's/cat/dog/g' animals.txt


## 🔍 `diff file1 file2`
Compares **two files** and tells you what's **different** between them.

```bash
diff file1.txt file2.txt
```

🧒 Like checking your homework vs your friend's version to see what changed!

---

## 📏 `wc filename`
Counts:
- 📄 Lines
- ✍️ Words
- 🔤 Characters

```bash
wc myfile.txt
```

👶 It's like measuring how big your story is!

---

## 🧠 `awk`
A smart tool that reads each line and lets you pick out parts or do something with them.

```bash
awk '{print $1}' file.txt
```

💬 Shows the **first word** on each line. Super useful!

---

## ✂️ `cut -d':' -f1 /etc/passwd`
Cuts each line into **pieces**, using a `:` separator, and shows only **part 1**.

```bash
cut -d':' -f1 /etc/passwd
```

🔧 Great for picking info from structured files.

---

## 📚 `sort filename`
Sorts the lines in a file:
- A-Z (default)
- Z-A with `-r`
- By numbers with `-n`

```bash
sort fruits.txt
sort -r numbers.txt
```

🍎📖 Like alphabetizing your school supplies list!

---

## ♻️ `uniq filename`
Removes duplicate **consecutive** lines. Sort first for best results!

```bash
sort names.txt | uniq
```

🧽 Cleans up repeated stuff.

---

## 📤 `tee filename`
Writes the output to **a file** and also shows it on the screen.

```bash
echo "Hello" | tee output.txt
```

📋 Copies and pastes at the same time!

---

## 🌳 `jq`
Reads and edits **JSON** data (a format computers love).

```bash
cat file.json | jq '.key'
```

🧙 Like a magic wand for computer data!

---

## ✅ Summary Table

| Command | What it Does | Like... |
|---------|---------------|---------|
| `diff`  | Shows differences between files | Spot the difference 🔍 |
| `wc`    | Counts lines, words, characters | File ruler 📏 |
| `awk`   | Reads and processes text smartly | Text brain 🧠 |
| `cut`   | Cuts parts of each line | Text scissors ✂️ |
| `sort`  | Sorts lines alphabetically/numerically | ABC sorter 📚 |
| `uniq`  | Removes repeated lines | De-duplicator ♻️ |
| `tee`   | Writes and shows output | Copy + show 📤 |
| `jq`    | Reads JSON | JSON whisperer 🌳 |

---

