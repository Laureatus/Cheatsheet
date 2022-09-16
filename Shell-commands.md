# Shell Commands

## cat
The command cat is used like more or less to output files to the terminal. However, cat is not as powerful as more or less so it is good for pipes or smaller files.

## cut
With cut certain sections of a file can be cut and printed.

Example

```
/etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
```


with the command cut -d: -f1 the usernames can be read out this way.

### cut example

```
$ cut -d : -f1 /etc/passwd
root
daemon
bin
```
-d defines where the text in fields should be separated. In this case a colon

-f defines which field should be printed. Here it would be the first field.


## head
With head the beginning of a document is printed.

With head -n 5 test.txt the first 5 lines of a file are printed.

With head -c 5 test.txt the first 5 bytes of the file are printed.

## less
With less the content of the whole file is printed like with Cat. An advantage of less is that you can navigate through the output text. Also very large files are already displayed even if the complete file is not yet loaded in memory.

 

## nl
nl shows the content of a file and the corresponding line numbers.

The correct syntax for nl is: nl [options] [file]

 
## od
With od files can be output in different formats.

With od -b [file] the file is converted to an octal format.

With -c into char format or with -d into decimal format or with -x into hexadecimal format

## Paste

With paste two or more files are concatenated.

For example, if two files exist the file countries with 5 countries and the file city with 5 cities the command would look like this:

paste countries city

The output of this command would look like this:

Switzerland Zurich

Germany Berlin

Italy Rome

Spain Madrid

Russia Moscow

 zzzzz

## sed
Sed can be used to manipulate files.

For example like this:

```sed s/A/B/g [filename]```
 

this would replace any letter A with B.

The g in the command stands for global which replaces all letters that match the search parameters. Otherwise only the first letter of each line would be replaced.

## sort
With Sort files can be sorted and output according to different options.

For example, a list of numbers can be sorted with ```sort -n```.

Here are some more options for sorting

```-d``` considers only alphanumeric characters

```-f``` ignore upper and lower case

```-h``` Compares human readable numbers (2k 1g)

```-M``` Sort by month

```-o``` output sort to a file

```-R``` sort in random order

```-r``` Sort in reverse order

## Split

split is used to split large files into smaller files. These files can be reassembled afterwards without any additional program.

To split a file into a predefined size the following command can be used:

 ```split -b [size] [filename] [filename2]```

with the command ```split -b 1MB [filename] [filename2]``` a 10MB file would be split into 10 smaller 1MB files.

## tail
tail performs the opposite function of head. Instead of printing the first 10 lines of a file, tail displays the last 10 lines. The default of 10 lines can be changed arbitrarily with the -n option.

## tr
Tr is derived from translate and is used to replace characters in text.

With the command ```tr 2 3 < [filename]``` every 2 would be replaced by a 3.

Other commands are:

```[:lower:]``` all lowercase letters

```[:upper:]``` all upper case letters

```[:digit:]``` all numbers

```[:alpha:]``` all letters

```[:blank:]``` all spaces

```-d``` delete characters

```-s``` replace several consecutive characters with a single one

## uniq
Uniq prints sorted files without duplicate lines. Uniq is mostly used together with sort.

```uniq [filename]``` prints the contents of the file without duplicate lines.

```uniq -d [filename]``` prints all duplicate lines.

```uniq -c [filename]``` shows how many times a line occurs.


## wc

The wc command can be used to count words characters and bytes in a text.

The syntax is:

```wc [options] [file]```

 The following options can be applied to wc:

```-l``` counts the lines

```-c``` counts the bytes

```-m``` counts the characters of a file

```-L``` prints the length of the longest line

```-w``` counts the words in the file

## grep
With grep files can be searched with the help of Reg-Ex.

The following syntax should be used:

```grep [options] pattern [file]```

There are also some predefined patterns which can be used:

```[:digit:]``` all digits 0-9

```[:upper:]``` all upper case letters

```[:lower:]``` all lowercase letters

```[:alpha:]``` all letters

```[:alnum:]``` all digits or letters

```[:punct:]``` all punctuation and special characters

```[:graph:]``` all graphic characters

```[:print:]``` printable characters

```[:blank:]``` spaces or tabs

```[:space:]``` characters that create white space

```[:cntrl:]``` all control characters

## find
The Find command can be used to search for files and directories and output them to the screen.

The following options are available:

```Find / [search term]``` searches everywhere

```Find /. [search term]``` searches all entries with the name of the search command in the current directory

```Find -name test.txt``` searches for files with the name test.txt

```Find -type d``` finds only directories

```Find -size -100c -ls``` searches for files smaller than 100 bytes

```Find / -user tom``` searches for all files of user tom

```Find -empty``` finds files and directories with size 0

## awk

Awk is a script language for editing and analyzing text.

The name is derived from the first letters of the developers. Aho, Weinberger and Kernighan.

 

The syntax of awk is as follows:

```Condition {statements}```

 

A usual condition would be a regular expression like e.g. ```/[0-9]+\.[0-9]+/```

A statement would then be e.g. ```'{print}'```.

A full command would be ```awk '/[0-9]+\.[0-9]+/ {print}' [filename]```

## pipes
With a pipe operator ```|``` the output of a command is directly forwarded to another command and used as input. So e.g. output of find can be sorted directly with Sort. But also more than two commands can be linked together.

## stdin,stdout,stderr
All commands executed in the terminal are assigned to three different channels.

The channel stdin has the number 0 and reads the input from the keyboard.

The channel stdout has the number 1 and writes output to the screen.

The channel stderr has the number 2 and writes output to the screen connected to the terminal.
