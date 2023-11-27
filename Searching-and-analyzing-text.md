# Searching and Analyzing Text
- Managing a Linux server involves many important steps and decisions based on data. Trying to gather the information you need in an agile and efficient manner is crucial.
- There are many Linux structures and tools that can help you incover the knowledge you seek.
## Processing Text Files
- Once you have found or created a text file, you may need to process it in some way to extract needed information. Understanding how to filter and format text will assist you in this endeavor.
## Filtering Text
- To sift through the data in a large text file, it helps to quickly extract small data sections. The cut utility is a handy tool for doing this. It will allow you to view particular fields within a file's records. The command's basic syntax is as follows:
    - cut OPTION... [FILE]...
- Before we delve into using this command, here are a few basics you should understand about the cut command:
    - ### Text File Records:
    - A text file record is a single file line that ends in a newline linefeed, which is the ASCII character LF. You can see if your text file uses this end-of-line character via the cat -E command. It will display every newline linefeed as a $. If your text file records end in the ASCII character NUL, you can also use cut on them, but you must use the -z option.
    - ### Text File Record Delimiter:
    - For some of the cut command options to be properly used, fields must exist within each text file record. These fields are not database-style fields but instead data that is separated by some delimiter. A delimiter is one or more characters that create a boundary between different data items within a record. A single space can be a delimiter. The password file, /etc/passwd, uses colons (:) to separate data items within a record.
    - ### Text File Changes:
    - Contrary to its name, the cut command does not change any data within the text file. It simply copies the data you wish to view and displays it to you. Rest assured that no modifications are made to the file.
- The cut utility has a few options you will use on a regular basis.
      - c, characters nlist: Display only the record characters in the nlist
      - b, bytes blist: Display only the record bytes in the blist.
      - d, delimiter: Designate the records's field delimiter as d. This overrides the tab default delimiter. Put d within quatation marks to avoid unexpected results.
      - f, fields flist: Display only the record's fields denoted by flist
      - s, only delimited: Display only records that contain the designated delimiter.
      - z, zero terminated: Designate the record end-of-line character as the ASCII character NUL.
- A few cut commands in action will help demonstrate its capabilities.
    - cut -d ":" -f 1,7 /etc/passwd
    - cut -c 1-5 /etc/passwd
- This text file employs colons (:) to delimit the fields within each record. The first use of the cut command designates the colon delimiter using the d option. Notice that the colon is encased in quotation makrs to avoid unexpected results. The -f option is used to specify that only fields 1 (username) and 7 (shell) should be displayed.
- The second example uses the -c option, in this case, the nlist argument is set to 1-5, so every records first five characters are displayed.
- #### Note: Occasionally it is worthwhile to save a cut command's output. You can do this by redirecting standards output, which is covered later in this chapter.
-  Another nice tool for filtering text is our old friend the grep command. The grep command is powerful in its use of regular expressions, which will really help with filtering text files.
    - The grep command's commonly used options
      - c, count: Display a count of text file records that contain a PATTERN match.
      - d, directories-action: When a file is a directory, if action is set to read, read the directory as if it were a regular text file; if action is set to skip, ignore the directory; and if action is set to recurse, act as if the -R, -r, or --recursive option was used.
      - E, extended-regexp: Designate the PATTERN as an extended regular expression.
      - i, --ignore-case: ignore the case in the PATTERN as well as in any text file records.
      - R, -recursive: Search a directory's contents, and for any subdirectory within the original directory tree, consecutively search its contents as well.
      - v, invert-match: Display only text files records that do not contain a PATTERN match.
- Many commands use regular expressions. A regular expression is a pattern template you define for utility, such as grep, which uses the pattern to filter text. Basic regular expressions (BREs) include characters such as a dot followed by an asterisk, to represent multiple characters and a signle dot to represent one character.
- They also use brackets to represent multiple characters, such as [a,e,i,o,u] or a range of characters, such as [A-z]. To find text file records that begin with particular characters, you can precede them with a caret (^) symbol. For finding text file records where particular characters are at the record's end, append a dollar sign ($) symbol to them.
- #### Note: You will see in documentation and technical descriptions different names for regular expressions. The name may be shortended to regex or regexp.
- Extended regular expressions (EREs) allow more complex patterns. For example, a vertical bar symbole (|) allows you to specify two possible words or character sets to match you can also employ parentheses to designate additional subexpressions.
## Formatting Text
- Often to understand the data within text files, you need to reformat file data in some way. There are a couple of simple utilities you can use to do this.
- The sort utility sorts a file's data. Keep in mind it makes no changes to the original file. Only the output is sorted. The basic syntax of this command is as follows"
        - sort [OPTION]... [FILE]...
- If you want to order a file's content using the system's standard sort order, simply enter the sort command followed by the name of the file you wish to sort.
- If a file contains numbers, the data may not be in the order you desire using the sort utility. To obtain proper numeric order, add the -n option to the command.
### The sort command's commonly used options
        - c, check: Check if file is already sorted. Produces no output if file is sorted. If file is not sorted, it displays the file name, the line number, the keyword disorder, and the first unordered line's text.
        - f, ignore-case: Consider lowercase characters as uppercase characters when sorting.
        - k n1, key=n1: Sort the file using the data in the n1 field. May optionally specify a second sort field by following n1 with a comma and specifying n2. Field delimiters are spaces by default.
        - M, month-sort: Display text in month of the year order. Months must be listed as standard three letter abbreviations, such as JAN, FEB, and so on.
        - n, numeric-sort: Display text in numerical order.
        - o, output=file: Create a new sorted file named file.
        - r, reverse: Display text in reverse sort order.
- The sort utility is handy for formatting a small text file to help you understand the data it contains. Another useful command for formatting small text files is one we've already touched on: the cat command.      
- The cat command's original purpose in life was to concatenate files for display. That is where it gets its name. However, it is typically used to display a single file.
- The cat utility foes not denote a file's beginning or end in its output.
- Another handy set of utilities for fromatting text are the pr and printf commands. The pr utility was covered in chapter 3.
- printf command's entire purpose in life is to format and display text data, it follows the basic syntax:
    - printf FORMAT [ARGUMENT]...
    - Employing the printf command
    - $ printf "%s\n" "Hello World"
- The printf command uses the %s\n as the formatting description. It is enclosed within quotation marks to prevent unexpected results. The %s tells printf to print the string of characters listed in the ARGUMENT, which in this example is Hello World. The \n portion of the Format tells the printf command to print a newline character after printing the string. This allows the prompt to display on a new line.
#### Note:
    - While the pr utility can handle formatting entire text files, the printf command is geared toward formatting the output of a single text line. You must incorporate other commands and write a Bash shell script for it to process a whole text file with it.
    - The printf command's commonly used FORMAT settings
        - %c: Display the first ARGUMENT character.
        - %d: Display the ARGUMENT as a decimal integer number.
        - %f: Display the ARGUMENT as a floating-point number.
        - %s: Display the ARGUMENT as a character string.
- Formatting text data can be useful in uncovering information. Be sure to play around with all these commands to get some worthwhile experience.
## Determining Word Count
- Besides formatting data, gathering statistics on various text files can also be helpful when you are managing a server. The easiest and most common utility for determining counts in a text file is the wc utility. The command's basic syntax is as follows:
    - wc [OPTION]... [FILE]...
- When you issue the wc command with no option and pass it a filename, the utility will display the file's number of lines, words, and bytes in that order.
- ### The wc command's commonly used options
    - c,--bytes: Display the file's byte count.
    - L, --max-line-length: Display the byte count of the file's longest line.
    - l, --lines: Display the file's line count
    - m, --chars: Display the file's character count.
    - w, --words: Display the file's word count.
- An interesting wc option for troubleshooting configuration files is the -L switch. Generally speaking, configuration file line length will be under 150 bytes, though there are exceptions. Thus, if you have just edited a configuration file and that service is no longer working, check the file's longest line length. A longer-than-usual line length indicates you might have accidentally merged two configuration file lines.
## Redirecting Input and Output
- When processing text and text files to help you to gather data, you may want to save that data. In addition, you may need to combine multiple refinement steps to obtain the information you need.
## Handling Standard Output
- It is important to know that Linux treats every object as a file. This includes the output process, such as displaying a text file on the screen. Each file object is identified using a file descriptor, an integer that classifies a process's open files. The file descriptor that identifies output from a command or script file is 1. It is also identified by the abbreviation STDOUT, which describes standard output.
- By default, STDOUT directs output to your current terminal. Your process's current terminal is represented by the /dev/tty file.
- A simple command to use when discussing standard output is the echo command. Issue the echo command along with a text string, and the text string will display to your process's STDOUT, which is typically the terminal screen.
- The neat thing about STDOUT is that you can redirect it via redirection operators on the command line. A redirection operator allows you to change the default behavior of where input and output are sent.
- For STDOUT, you redirect the output using the > redirection operator.
- #### Warning:
    - If you use the > redirection operator and send the output to a file that already exists, that file's current data will be deleted. Use caution when employing this operator.
- To append data to a preexisting file, you need to use a slightly different redirection operator. The >> operator will append data to a preexisting file. If the file does not exist, it is created and the outputted data is added to it.
## Redirecting Standard Error
- Another handy item to redirect is standard error. The file descriptor that identifies a command or script file error is 2. It is also identified by the abbreviation STDERR, which describes standard error. STDERR, like STDOUT, is by default sent to your terminal (/dev/tty).
- The basic redirection operator to send STDERR to a file is the 2> operator. If you need to append the file, use the 2>> operator.
- #### Tip:
    - Sometimes you want to send standard error and standard output to the same file. In these cases, use the &> redirection operator to accomplish the goal.
    - If you don't care to keep a copy of the error messages, you can always throw them away. This is done by redirecting STDERR to the dev/null file. The /dev/null file is sometimes called the black hole. This name comes from the fact that anything you put into it, you cannot retrieve.
## Regulating Standard Input
- Standard input, by default, comes into your Linux system via the keyboard or other input devices. The file descriptor that identifies an input into a command or script file is 0. It is also identified by the abbreviation STDIN, which describes standard input.
- As with STDOUT and STDERR, you can redirect STDIN. The basic redirection operator is the < symbol. The tr command is one of the few utilities that require you to redirect standard input.
- A practical example of redirecting STDOUT and STDIN involves the diff utility. The diff utility allows you to discover any disparities between two text files and change the differing text file so that the two files are identical.
#### Commonly used redirection operators
- >: Redirect STDOUT to specified file. If file exists, overwrite it. If it does not exist, create it.
- >>: Redirect STDOUT to specified file. If file exists append to it. If it does not exist, create it.
- 2>: Redirect STDERR to specified file. If file exists, overwrite it. If it does not exist, create it.
- 2>>: Redirect STDERR to specified file. If file exists, append to it. If it does not exist, create it.
- &>: Redirect STDOUT and STDERR to specified file. If file exists, overwrite it. If it does not exist, create it.
- &>>: Redirect STDOUT and STDERR to specified file. If file exists, append to it. If it does not exist, create it.
- <: Redirect STDIN from specified file into command.
- <>: Redirect STDIN from specified file into command and redirect STDOUT to specified file.
## Piping Commands
- If you really want to enact powerful and quick results at the Linux command line, you need to explore pipes. The pipe is a simple redirection operator represented by the ASCII character 124(|), which is called the vertical bar, vertical slash, or vertical line.
- With the pipe, you can redirect STDOUT, STDIN, and STDERR between multiple commands all on one command line. Now that is powerful redirection.
- The basoc syntax for redirection with the pipe symbol is as follows:
    - command 1 | command 2 |...
- The syntax for pipe redirection shows that the first command, command1, is executed. Its STDOUT is redirected as STDIN int the second command, command2. Also you can pipe more commands together than just two.
- Keep in mind that any command in the pipeline has its STDOUT redirected as STDIN to the next command in the pipeline.
## Creating Here Documents
- Another form of STDIN redirection can be accomplished using a here document which is sometimes called here text or heredoc.
- A here document allows you to redirect multiple items into a command. It can also modify a file using a script, create a script, keep data in a script, and so on.
- A here document redirection operator is << followed by a keyword. This keyword can be anything, and it signals the beginning of the data as well as the data's end.
#### Employing a here document wit the sort command
- $ sort <<EOF
- > dog
  > cat
  > fish
  > EOF
- cat
- dog
- fish
- $
- The sort command is entered followed by the << redirection operator and a keyword, EOF. The enter key is pressed, and a secondary prompt,>, appears, indicating that more data can be entered. Three words to be sorted are entered. The keyword, EOF, is entered again to denote that data entry is completed. When this occurs, the sort utility alphabetically sorts the words and displays the results to STDOUT.
## Creating Command Lines
- Creating command line commands is a useful skill. There are several different methods you can use. One such method is using the xargs utility.
- By piping STDOUT from other commands into the xargs utility, you can build command-line commands on the fly.