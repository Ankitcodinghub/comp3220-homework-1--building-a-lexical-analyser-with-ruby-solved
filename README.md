# comp3220-homework-1--building-a-lexical-analyser-with-ruby-solved
**TO GET THIS SOLUTION VISIT:** [COMP3220 Homework 1- Building a Lexical Analyser with Ruby Solved](https://www.ankitcodinghub.com/product/comp3220-building-a-lexical-analyser-with-ruby-solved-2/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;118105&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;COMP3220 Homework 1- Building a Lexical Analyser with Ruby Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
The grammar rules for the language “TINY” are listed below. In this assignment we will identify the tokens in this language and build a lexical analyser (lexer) for recognizing and outputting TINY tokens.

# https://www.cs.rochester.edu/~brown/173/readings/05_grammars.txt #

# “TINY” Grammar #

# PGM –&gt; STMT+

# STMT –&gt; ASSIGN | “print” EXP

# ASSIGN –&gt; ID “=” EXP

# EXP –&gt; TERM ETAIL

# ETAIL –&gt; “+” TERM ETAIL | “-” TERM ETAIL | EPSILON

# TERM –&gt; FACTOR TTAIL

# TTAIL –&gt; “*” FACTOR TTAIL | “/” FACTOR TTAIL | EPSILON

# FACTOR

# –&gt; “(” EXP “)” | INT | ID

# ID –&gt; ALPHA+

# ALPHA –&gt; a | b | … | z or

# A | B | … | Z

# INT –&gt; DIGIT+

# DIGIT –&gt; 0 | 1 | … | 9

# WHITESPACE –&gt; Ruby Whitespace

Whenever a token is identified, we encapsulate it using the Token class below. Each token has a type and text. For example, if DOG was identified as a variable in this language, it could have type “id” and

text “DOG”. The add operator might have type “addOp” and text “+” or type “+” and text “+”. These values are somewhat arbitrary – choose values that make sense to you.

Token Class

I have given you a partially complete Token class that you should modify for this assignment called “TinyToken.rb”. It has a few constants already defined. The VALUES of these variables represent the name of the token. You will need to build more constants to store all of the tokens that exist in this language. For this assignment, you get to decide what categories of lexemes there are and what you want to name those categories.

It is important to test all the code you write. At the very least, use “puts” to test the class methods. You can build the tests in separate files and load them as needed: load “mytest.rb”. The code below tests the Token class methods.

# Test the Token class

tok = Token.new(“atype”,”atext”) puts “Token type: #{tok.type}” puts “Token text: #{tok.text}” tok.type = “btype” tok.text = “btext” puts “Token type: #{tok.type}” puts “Token text: #{tok.text}” puts “Token: #{tok}”

The “Lexer”

The first goal is to build a Scanner (or Lexer) for TINY. I have sketched the basic structure in file named “TinyScanner.rb”. Here are a few points to consider:

1) The constructor is passed a file name which contains the source code for a TINY program. The constructor opens the file and reads the first character, storing it in class variable @c (which acts as a one-character look ahead). I already did this.

2) Currently, the Scanner abends if it is passed a file that doesn’t exist. Modify the code so that it fails gracefully in this circumstance.

3) Method nextCh() updates @c with the next character and returns it, unless it has reached the end of the file, in which case it will return “eof”. I already did this.

4) Method nextToken() returns the next token identified by the scanner. It is not complete, as it does not identify all Tokens in your grammar yet. In addition to identifying and returning a token, this method should print what it finds, each time it identifies a token (just like the example of the lexer in the PowerPoint for chapter 4). You must complete this method.

5) Contiguous whitespace should be combined and emitted as a single token. I already did this for you.

6) An end of file (EOF) token should be emitted when the file has been completely processed. I already did this for you.

7) There are several helper methods defined at the bottom of “TinyScanner.rb” that you can use to help you to identify different types of characters (like numbers, letters, and whitespace).

Display and Print Tokens

I’ve included a file called “TestTinyLexer.rb” that you can use to test your lexer (previous section). For the time being, it simply scans a file and stores all of the tokens in a text file called “tokens”. Feel free to modify this file to test different things about your lexer, or to open the tokens file to see what was actually saved.

I’ve also included a sample input file (input.txt) that adheres to our TINY programming language. You should experiment with different inputs that both adhere to and don’t adhere to the grammar to verify the correctness of your lexer.

Sample Program Output

Below is a screenshot of sample output that would result from using the included sample input file.
