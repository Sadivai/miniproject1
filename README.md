#first function e input neo
def take_input():
    name = input("Enter your name: ")
    cls = input("Enter your class: ")
    section = input("Enter your section: ")
    email = input("Enter your email: ")
    aim = input("Enter your aim: ")
    phone = str(input("Enter your phone number: "))
    district = input("Enter your district: ")
    
    student = {
            "name": name,
            "cls": cls,
            "section": section,
            "email": email,
            "aim": aim,
            "phone": phone,
            "district": district
        }
    return student

#prothom function er returned value ebr second function e pathao

def show_profile(student):

    print( "===" * 15)
    print("            Student Profile")
    print( "===" * 15)
    for key ,value in student.items():
        print(key,"-",value)
    print( "===" * 15)
student = take_input()
 #take_input function call kore student dictionary e store kora hoyese
show_profile(student)

aliases = {
                "nam": "name",
                "nme": "name",

                "class": "cls",
                "clss": "cls",
                
                "phn": "phone",
                "fon": "phone",
                "phne": "phone",
                "number": "phone",

                "aims": "aim",

                "sctn": "section",
                "sec": "section",
                "group" : "section",
                "grp" : "section",

                "dstrct": "district",
            }

mandatory_fields = ["name", "aim", "phone", "section"]


def update_profile(student):
    while True:

        choice = input("Do u want to make any changes in ur profile?(yes/no):").lower()
    
        if choice == "no":
            print("Thank you for using our service!")
            break
            
        elif choice == "yes":
            key = input("Which Do u want to update?").lower()
            new_value = input(f"Enter new value for {key}: ")
                       
            key = aliases.get(key, key)

            if key in mandatory_fields and new_value == "":
                print(f"{key} is a mandatory field which can't be empty")
                
            elif key in student and key not in mandatory_fields:
                student[key] = new_value
                print(f"{key} has been updated to {new_value}.")   
            elif key in mandatory_fields and new_value != "":
                student[key] = new_value
                print(f"{key} has been updated to {new_value}.")         
            else:
                student[key] = new_value
                print(f"{key} has been added to your profile with value {new_value}.")
        else:
            print(f"{choice} is not a valid option.Thank for using us.")
    return student
student = update_profile(student)
show_profile(student)
