# Unix Pipelines Field Guide

## Understanding Unix Pipelines


For unix, commands are meant to only do one thing well. `|` takes the input from the left command an gives to to the command on its right.

`|` is diferent from `>` because `|` links commands together wheras `>` saves the output of a command to a file.

---

## Five Useful Pipeline Examples

### 1
```bash
find . -type f | grep "\.md$" | wc -l
```

it lists all the markdown files in the folder. `grep` filters out everything except files ending in `.md` and `wc -l` counts the remaining lines.
You can use this and modifications of this to find the number of certain files, lets say you want to see how many raw photos you have, so `.rw2`. 

### 2

```bash
du -sh * | sort -hr | head -n 3
```

`du` calculates the storage size of all items, `sort -hr` sorts those sizes from largest to smallest, and `head -n 3` keeps only the top three results.
A developer uses this to find what is taking up their disk space or repo spce.

### 3
```bash
cat example.json | grep name | wc -l
```

`cat` gives the text from `example.json` then `grep name` finds every single time name is mentioned, and then `wc -l` gives how many lines there are so this pipeline gives how many times "name" appears in `example.json`.

### 4

```bash
history | grep cd
```

`history` gets the history of the commands executed in the terminal. `grep cd` finds all commands executred with cd in them. 

### 5
```bash
cat example.json | grep name | cut -f 2 -d ':'
```
`cat` gives the contents of the file, `grep` gives finds all the lines with the word name, `cut -f 2 -d 'd'`, it gives column 2 with the deliniater for columns being `:`.