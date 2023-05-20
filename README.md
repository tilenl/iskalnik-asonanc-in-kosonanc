### Preprocessing step, that was done:

```bash
cat besede.txt | sed "s/<br>$//" > besede_modified.txt
```

#### Explanation:

```bash
cat besede.txt # read the content of the file and outputs it to the standard output

| # captures the standard output of the previous command (cat) and rerouts it to he standard input of the next command (sed)

sed "s/<br>$//" # regex expression, which searches at the end of the line ($) for the '<br>' substring, replacing it with nothing (//, anything that goes between these is placed instead of <br>)

> besede_modified.txt # reroutes the standard output of the previous command (sed) to write to the file, creating it if it does not already exist
```

#### Usage of the processed words:

Works on besede as well as on besede_modified.txt

```bash
cat besede_modified.txt | grep -E "a.i\b" | less # match any character between "a" and "i"

grep "a[^t]i\b" besede_modified.txt | less # match any word that ends with "a" "i" and between is any character BUT "t"
```

OR just use

```bash
grep "a.i\b" besede_modified.txt | less
```

### Explanation:

```bash
cat besede_modified.txt # read the content of the file and outputs it to the standard output

grep -E "a.i\b"
# grep searches any given input file, selecting lines that match one or more patterns (man grep)
# -E means it uses extended search (works without it as well, as we aren't using any extended functionalities)
# "a.i\b" searches for lines that contain character "a" than any word "." and character "i" at the end of the word "\b" (from back).

less # makes the output scrollable, if there are so many word, the command line can't output them all at once
```