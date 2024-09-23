# Artificial_Intelligence - In construction for now
Repository of AI stuffs and affiliates.

Textual part - Before starting - 
# Regular Expression (RegEx) :

\n : New Line 
\t : New Tab

print(r'stuff') ==> Priting the whole string and character even regex expressions. 


In python, we'll use the library re

# Introduction
re.compile : 
Function which convert a regular expression pattern into a regular expression object. After that we'll be able to use this regex object to perform pattern matching like .match(), .search(), .findall() or .finditer()
*** Keeping in mind that regex are case-sensitive. *** To avoid that we can use flags in re.compile like re.compile(r' string stuff' , re.IGNORECASE) for being case-insensitive.

# Special character :
'.' : used for getting any character . For only getting . we need to use '\."
\d : used for matching decimal digit <=> [0-9]
\D : used for matching non decimal digit <=> [^0-9]
\s : used for matching whitespace character <=> [\t\n\r\f\v]
\S : used for matching non-whitespace character <=> [^\t\n\r\f\v]
\w : used for matching alphanumeric character and underscore <=> [a-zA-Z0-9_]
\W : used for matching non-alphanumeric character <=> [^a-zA-Z0-9_]
\b : used for defining a boundary i.e. an non-alphanumeric character, whitespace, beginning or end of a string. Ex : \bgroup ==> We can search for 'group' alone or 'group + string'

MetaCharacter
^ + 'some string' : ^ is used to match the string expression located at the beginning of the string - sentence
$ + 'some string : $ is used to match the string expression located at the end of the string - sentence
[regex expression]+ : + is used to say one or more repetition of the previous regex expression

# Then we can mixte all those expression to get what regex we want :
For example if we want to match all the different type of phonenumber within a text we can use :
 - re.compile(r'\d{2}[- ]\d{2}[- ]\d{2}[- ]\d{2}[- ]\d{2}'} ==> The result will be like 01-45-24-78-29 or 01 45 24 78 29
 - re.compile(r'\d{2}[- ]\d{2}[- ]\d{2}[- ]\d{2}[- ]\d[^6-9]'} ==> Matching regular phone number which doesn't finish by 6, 7, 8, or 9

# Complicated patterns :
? : is used for mathing the previous expression or not.
 - re.compile(r'Mr\.?) ==> We'll match "Mr." or "Mr"

We can compile regex stuff together : 
 - re.compile(r'Mr\.?\s[A-Z]\w*') ==> Will match every 'Mr.' + whitespace + Capital letter + string expression or 'Mr' + whitespace + Capital letter + string expression

( ) : is used for defined a group of string. We can use (Mr|Mister) to match Mr or Mister string expression


# Substitution to modify string
re.compile(r' some expression') + .sub(r' some other expression to remplace the regex one', the sample text)
Example : We need only first and third group
sample = """
AAAAAA BBB CCC
AAA DDDDDD
AAAA EE FFFFFF
"""

regex = re.compile(r'([a-zA-Z]+)[ ]?([a-zA-Z]+)?[ ]([a-zA-Z]+)') ==> Meaning getting the first group of letter, the first whitespace is optionnal, the second group of letter is optionnal, the second whitespace is mandatory and the third group of letter is mandatory.
new = regex.sub(r'\1 \3', sample) ==> We will only keep the first and the third group of letter


