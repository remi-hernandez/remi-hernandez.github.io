= Python regex
:hp-tags: python, regex

==== sub()

Change a value by another with sub.
We will rewrite the sentence in order to write the group1 followed by "pipou"

[source,python]
----
import re

test = "56test"

# this will write the first group of the regex followed by pipou in test string 
print re.sub(r"([0-9]{2})([a-z]{4})", r"\g<1>pipou", test)

#>>'56pipou'
----

The same thing by compiling first : 

[source,python]
----
import re

test = "56test"

# this will replace the first group of the regex by pipou in test string 
regex = re.compile(r"([0-9]{2})([a-z]{4})")
print regex.sub(r"\g<1>pipou", test)

#>>'56pipou'
----

==== change stuff in a file with regex 

Example - changing the number 183200 of the first line to 201600 in multiples files containing multiple texts like this

WSCI31 RCTP 183200
RCAA SIGMET 2 VALID 190500/190900 RCTP-
RCAA TAIPEI FIR EMBD TS FCST
WI N2630 E11730 - N2800 E12400 - N2400 E12400 - N2500 E11730
TOP FL410 MOV E 10KT NC


[source,python]
----
    import re
   
    file_list = ["6420.txt", "6421.txt" ,"6422.txt" ,"6423.txt" ,"6440.txt"
        ,"6441.txt" ,"6442.txt" ,"6443.txt" ,"6444.txt" ,"6445.txt"
        ,"6446.txt" ,"6447.txt" ,"6448.txt" ,"6449.txt" ,"6450.txt"
        ,"6451.txt" ,"6452.txt" ,"6453.txt", "6454.txt"]

    new_date = str(input("enter a new date>"))
    regex = re.compile(r"((WC|WS|WV)[A-Z]{2}\d{2})\s+([A-Z]{4})\s+([0-9]{6})\s+(CC[AB])?")

    for sigmet in file_list:
        file_name = "./" + sigmet

        f = open(file_name, "r")
        content = f.read()
        # we will write the groups 1 and 3 follwed by the new date
        new_content = regex.sub(r"\1 \3 " + new_date + r"\n", content)
        f.close()

        f = open(file_name, "w")
        f.write(new_content)
        f.close()
----

==== findall()

This function find all occurences of a pattern.
Note at the end of the regex : `((?![\(,]).|\s)*[\(,]))` this part will look for every character except '(' and ','.

[source, python]
----
def get_sigmets_in_string_list(string_to_parse):
    compiled_regex = re.compile(r'(((((WC|WS|WV)[A-Z]{2}\d{2})\s+([A-Z]{4})\s+([0-9]{6})\s+(CC[AB])?)(([A-Z]{4})\s+SIGMET\s+((\w+\s+){1,})VALID\s+(([0-9]{6})\/([0-9]{6}))\s+([A-Z]{4}-))((?![\(,]).|\s)*[\(,]))')
    sigmet_list = compiled_regex.findall(string_to_parse)
    cleaned_list = []
    for sigmet in sigmet_list:
        tmp_list = list(sigmet[0])
        tmp_list[len(tmp_list) - 1] = '='
        cleaned_list.append("".join(tmp_list))

    #for sigmet in cleaned_list:
    #    print("\n\nsigmet : [{}]".format(sigmet))

    return cleaned_list
    
----

