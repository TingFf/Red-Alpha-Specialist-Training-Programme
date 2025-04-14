# Red-Alpha-Specialist-Training-Programme

This marks the beginning of my journey as a Cyber Security Specialist. I chose to undergo the Red Alpha Specialist Training Programme because I believe it offers the best pathway for someone like me, who is starting out without prior industry experience. I am committed to making the most of this opportunity, with the goal of building a strong foundation in cyber security. Through this programme, I hope to gain hands-on skills, real-world exposure, and the confidence needed to progress into a mid-level cyber security role by the time I complete my training. I am excited to continuously learn, grow, and contribute to the field as I develop both technical expertise and professional resilience.

This repository serves as a place to document the work I’ve completed and the knowledge I’ve gained throughout this journey. I also plan to share some of my personal experiences and insights here as I continue to grow in the field.

Python Notes:  
Everything is python is a object.  
Objects topic:  
1.  
== checks equality.    
is checks identity. Check whethers is it pointing the same object.  
2.  
def create_looney_tune(name="cool guy!", friends_list=[], age=0): # Default mutable list.  

bugs = create_looney_tune("Bugs Bunny", age=2)  # Both bugs and daffy use the same default list.  
daffy = create_looney_tune("Daffy Duck")

add_new_friend(daffy, bugs)    # Adding daffy friend list will modify bugs friend list as well  
add_new_friend(yosemite, daffy)

Answer:

Looney Tune structure:
[name, friends_list, int]
name - str, friends_list - list, age - int
NAME = 0
FRIENDS_LIST = 1
AGE = 2

...
def show_looney_friends(looney_tune):
    """this function shows the friends of a given looney tune"""
    if len(looney_tune[FRIENDS_LIST]) == 0:  # This line will give error if the below condition is not implement and just return ["Bugs_Bunny", None, 0]
        print("%s has no friends :(" % (looney_tune[NAME],))
...
def create_looney_tune(name="cool guy!", friends_list=None, age=0): # Change to None.  
""" To prevent using the same object list, set the friends_list = None but none type cant be process later on so have to use this condition to change back and this ensure not the same object """
if friends_list is None:
    friends_list = []
return [name, friends_list, age]
...


