#!/usr/bin/python3
import sys
import getopt
import random

with open('words.txt', "r") as file:
    lines = file.readlines()
for i in range(len(lines)):
    lines[i] = lines[i].strip()

def arg_handler(argv):
    w, c, n, s = "", "", "", ""
    arg_help = "usage: xkcdpwgen [-h] [-w WORDS] [-c CAPS] [-n NUMBERS] [-s SYMBOLS]\n\nGenerate a secure, memorable password using the XKCD method\n\noptional arguments:\n"
    arg_help += "   - h, --help\n        show this help message and exit\n"
    arg_help += "   -w WORDS, --words WORDS\n        include WORDS words in the password (default=4)\n"
    arg_help += "   -c CAPS, --caps CAPS\n        capitalize the first letter of CAPS random words (default=0)\n"
    arg_help += "   -n NUMBERS, --numbers NUMBERS\n        insert NUMBERS random numbers in the password (default=0)\n"
    arg_help += "   -s SYMBOLS, --symbols SYMBOLS\n        insert SYMBOLS random symbols in the password (default=0)\n"
    
    try:
        opts, args = getopt.getopt(argv[1:], "hw:c:n:s:", ["help=", "words=", "caps=", "numbers=", "symbols="])
    except:
        print(arg_help)
        sys.exit(2)
    for opt, arg in opts:
        if opt in ("-h", "--help"):
            print(arg_help)
            sys.exit(2)
        elif opt in ("-w", "--words"):
            w = arg
        elif opt in ("-c", "--caps"):
            c = arg
        elif opt in ("-n", "--number"):
            n = arg
        elif opt in ("-s", "--symbols"):
            s = arg
    print(pw_gen(w,c,n,s))
    
def pw_gen(w, c, n, s):
    pw = random.sample(lines, 4) if w == "" else random.sample(lines, int(w)) # make base pw
    for i in random.choices(range(0,len(pw)), k = (0 if c == "" else int(c))):
        pw[i] = pw[i].capitalize() # add caps
    for i in random.choices(range(0,len(pw) + 1), k = (0 if n == "" else int(n))): 
        pw.insert(i, str(random.randint(0,9))) # add numbers
    for i in random.choices(range(0,len(pw) + 1), k = (0 if s == "" else int(s))):
        pw.insert(i, str(random.choice(['~','!','@','#','$','%','^','&','*','.',':',';']))) # add symbols
    return ''.join(pw)

if __name__ == "__main__":
    arg_handler(sys.argv)