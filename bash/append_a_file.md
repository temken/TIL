# Define a target-specific macro

In order to append a line of text to a text file, we can simply run

```bash
echo "new text" >> textfile.txt
```

This appends the text file by one line.

Beware that the command
```bash
echo "new text" > textfile.txt
```

with ```>``` instead of ```>>``` replaces the entire content of the file with the new text.

If the text contains quotation marks ```"```, one has to write them with a backslash ```\"```.


## Source

[AskUbuntu thread on appending](https://askubuntu.com/questions/21555/command-to-append-line-to-a-text-file-without-opening-an-editor)

[AskUbuntu thread on quotes](https://askubuntu.com/questions/20034/differences-between-doublequotes-singlequotes-and-backticks-on-comm)
