# Red-Alpha-Specialist-Training-Programme

This marks the beginning of my journey as a Cyber Security Specialist. I chose to undergo the Red Alpha Specialist Training Programme because I believe it offers the best pathway for someone like me, who is starting out without prior industry experience. I am committed to making the most of this opportunity, with the goal of building a strong foundation in cyber security. Through this programme, I hope to gain hands-on skills, real-world exposure, and the confidence needed to progress into a mid-level cyber security role by the time I complete my training. I am excited to continuously learn, grow, and contribute to the field as I develop both technical expertise and professional resilience.

This repository serves as a place to document the work I’ve completed and the knowledge I’ve gained throughout this journey. I also plan to share some of my personal experiences and insights here as I continue to grow in the field.

## Python Notes:  
Everything is python is a object.  
## Topics
**Objects**  
`==` checks equality.    
`is` checks identity. (Is it pointing to the same object in memory)
```
def create_looney_tune(name="cool guy!", friends_list=[], age=0): # Default mutable list. (Bug)
def create_looney_tune(name="cool guy!", friends_list=None, age=0): # Set to None (Solution#1)

bugs = create_looney_tune("Bugs Bunny", age=2)  # Both bugs and daffy use the same default list.  
daffy = create_looney_tune("Daffy Duck")

add_new_friend(daffy, bugs)    # Adding daffy friend list will modify bugs friend list as well  
add_new_friend(yosemite, daffy)
...
if friends_list is None:  (Solution#2)
    `friends_list = []  
return [name, friends_list, age]
...  
```
**Modules**  
`from datetime import datetime, timedelta`
```
import sys
...
userinput = sys.argv[1:]  # Takes all the input from command line until user hits enter
operator = userinput[0]
```
```
import argparse
import sys


def add(num1, num2):
    return num1 + num2


def sub(num1, num2):
    return num1 - num2


def mul(num1, num2):
    return num1*num2


def div(num1, num2):
    return num1/num2


def get_arguments():
    parser = argparse.ArgumentParser(    # This creates the basic skeleton of the argument parser.
        prog='command_calculator.py',
        usage='%(prog)s [-h] [-w] (add,sub,mul,div) first_number second_number',
        )    
    parser.add_argument(                 # (First argument since initialize first) Ensures user enter the choices indicated in the the function otherwise will auto display error
        "operation",                     # Argument varible
        choices=["add", "sub", "mul", "div"],
        metavar="(add.sub.mul.div)",    # To display different when user using -h
        help="operation to perform"
    )
    parser.add_argument(                # If option is provided, will return True.
        "-w", "--wrap",
        action="store_true",
        help="wrap the result in a message"
    )
    parser.add_argument("first_number", type=float, help="first operand")  # (Second argument since initialize second)
    parser.add_argument("second_number", type=float, help="second operand")    # (Third argument since initialize third)

    group = parser.add_mutually_exclusive_group()           # Those within the group cant exist together.
    group.addargument("-v", "--verbose", help="description")       
    ...
    

    if len(sys.argv) == 1:              # File path/name == sys.argv[0]
        parser.error("too few arguments")
    args = parser.parse_args()
    return args

"""
def test():
    args = get_arguments()
    args.first_number = 6.0
    args.second_number = 3.0

    assert add(args.first_number, args.second_number) == 9.0
    assert sub(args.first_number, args.second_number) == 3.0
    assert mul(args.first_number, args.second_number) == 18.0
    assert div(args.first_number, args.second_number) == 2.0
    print("All test passed")
    return
"""

def main():
    args = get_arguments()
    test()
    if args.wrap:
        print("Good morning :)")
    match args.operation.lower():
        case "add":
            print(add(args.first_number, args.second_number))
        case "sub":
            print(sub(args.first_number, args.second_number))
        case "div":
            print(div(args.first_number, args.second_number))
        case "mul":
            print(mul(args.first_number, args.second_number))
    return


if __name__ == "__main__":
    main()
```
**Regular expression**

1. RE works on string.  
2. More efficient way of string searching without much manipution on the string.  
3. character class`(/d, /w)` only works on single char unless uses quatifier.`(+, *)`
```
import re

re.search("...", s) -> return None if no search result
```

```
return re.sub("road", "Rd.", s, flags=re.IGNORECASE) -> case-insensitive
```
4. Remove leading zeros of an ip address
```
def re19(s):
    return re.sub(r'\b0+(\d)', r'\1', s)

1st Argument:
\b — word boundary (ensures we’re at the start of a number segment)
0+ — one or more leading zeros
(\d) — captures the first digit after the zeros

2nd Argument:
\1 - Replace with capture digit
```
5. Only `re.match()`, `re.search()`, `re.fullmatch`, `re.finditer()` returns a match object.
6. Negative lookbehind match any thing not at the beginning of the string.
```
import re

s = "JSONData"
snake = re.sub(r'(?<!^)([A-Z])', r'_\1', s).lower()
print(snake)


Position | Char | (?<!^) Passes? | Capital? | Match?
    0    |  J   |     ❌         |   ✅    | ❌
    1    |  S   |     ✅         |   ✅    | ✅
    2    |  O   |     ✅         |   ✅    | ✅
    3    |  N   |     ✅         |   ✅    | ✅
    4    |  D   |     ✅         |   ✅    | ✅
    5    |  a   |     ✅         |   ❌    | ❌
    6    |  t   |     ✅         |   ❌    | ❌
    7    |  a   |     ✅         |   ❌    | ❌

```
7. 
```
return " ".join(re.findall(fr"[\S]{{{limit+1},}}", s))
```
**List Comprehension**
1. When need return a list.
2. Typical structure. 
```
list = []
for words in list_of_strings:
    if re.search(words, s):
         list.append(words)
    return list
...

equivalent

return [words for words in list_of_strings if re.search(words, s)]
```
3. Hex encoder and decoder.
```
def hex_decode(string):
    "This function decodes each char to hex bytes"
    return bytes.fromhex(string).decode('utf-8')

def hex_encode(string):
    "This function encodes each char to hex bytes"
    return string.encode('utf-8').hex()

```

4. Nested list comprehension.
```
[[y*x for y in range(5)] for x in range(5)]
```
5. Ascii encoder and decoder.
```
def ascii_codes(string):
    "This function encodes each char to its ascii value"
    return [i for i in string.encode("ascii")] --> This will convert the encoded bytes in decimal

or


def ascii_codes(string):
    "This function encodes each char to its ascii value"
    return [ord(i) for i in string]
```

**Magic Function**
1. Lambda
```
div_and_mod = lambda x, y: (x / y, x % y) 
non_negative = lambda x: x if x > 0 else 0

assert div_and_mod(4, 2) == (2.0, 0)
assert non_negative(1) == 1
assert non_negative(-1) == 0

...
```
2. Map
```
world_map = lambda x: x.casefold().capitalize()

def main():
    countries = ['ISRAEL', 'france', 'engLand', 'sinGAPore']
    assert list(map(world_map,countries)) == ['Israel', 'France', 'England', 'Singapore']
```
