# Lab 4 Report 

Consider the following three markdown snippets:

Snippet 1

`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)

Snippet 2

[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)

Snippet 3

[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text

## Link to my markdown-parse repository here:
[Markdown-Parser Repository](https://github.com/cerealb/markdown-parser.git)

## Snippet 1
### Expected Output 
error, 'google.com, 'cod[e'] (displayed as a link), 'code]' (displayed as a link) 
### Code in MarkdownParseTest.java
![Capture](https://user-images.githubusercontent.com/103210460/171123627-23301cb2-1b33-4aeb-977e-0d79a9f97c92.JPG)

### Implementation 
the section of the MakeFile that will not pass will be : java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest

this will be because the testfile will be able to compile, but not run

### Answers
Yes, I believe that a code change will be possible to be made for the backticks. In the actual file itself (MarkdownParse.java), there is a chunk of code in which follows: 

            int openBracket = markdown.indexOf("[", currentIndex);
            int closeBracket = markdown.indexOf("]", openBracket);
            int openParen = markdown.indexOf("(", closeBracket);
            int closeParen = markdown.indexOf(")", openParen);
            
this block of code allows the parantheses and brackets pass through. Obviously I haven't implemented the actual code, but having at least 4 lines of code to cover the different placements where the backticks would be could possibly fix the error output. 

## Snippet 2
### Expected Output 
a.com, a.com(()), example.com 
### Code in MarkdownParseTest.java
![Capture](https://user-images.githubusercontent.com/103210460/171126808-843ae06c-de4c-4d69-8ac5-fa7581902606.JPG)

### Implementation 
passed 
### Answers
There is already a piece of code that will bypass the parentheses, brackets, and escaped brackets. The following block of code: 

            int openBracket = markdown.indexOf("[", currentIndex);
            int closeBracket = markdown.indexOf("]", openBracket);
            int openParen = markdown.indexOf("(", closeBracket);
            int closeParen = markdown.indexOf(")", openParen);
     
already allows the code to digest the parentheses, brackets, and escaped brackets. 

## Snippet 3
### Expected Output 
error, this title text is really long and takes up more than one line (displayed as a link), error
### Code in MarkdownParseTest.java
![Capture](https://user-images.githubusercontent.com/103210460/171127767-7499788b-dd4e-44e3-a07a-4492fd9bb8c8.JPG)

### Implementation 
the section of the MakeFile that will not pass will be : java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest

this will be because the testfile will be able to compile, but not run 
### Answers
No, I believe that this code change will be need more than 10 lines of code. This is because the code will still process the testfiles even if there is a lot of spacing, therefore the problem in the testfile is not the amount of lines. The problem in the testfile would be the way the testfile is actually structured. 
