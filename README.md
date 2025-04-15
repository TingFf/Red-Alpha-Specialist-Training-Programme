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
"""
