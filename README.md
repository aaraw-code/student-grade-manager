# student-grade-manager
 project to manage student grades, subjects, and performance.


class student:
    def __init__(self,name):
        self.name = name
        self.grades = {}                     

    def add_grade(self,subject,grade):
        self.grades[subject] = grade          #Save the grade for subjects

    def get_average(self):
        if not self.grades:
            return 0
        else:
            return sum(self.grades.values()) / len(self.grades)

    def show_details(self):
        print("name", self.name)
        print("Grades:")
        for subject,grade in self.grades.items():
            print(f"{subject}:{grade}")
        average = self.get_average()
        print("Average Grade:", average)

students = {}

while True:
    print("1: Add student")
    print("2: Add grade to a student")
    print("3: View student detail")
    print("4: Exit")
        

    choice = input("Enter your choice(1-4): ")

    if choice == "1":
        name = input("Enter student name: ")
        students[name] = student(name)
        print("student added.")

    
    if choice == "2":
        name = input("Enter student name: ")
        if name in students:
            while True:
                subject = input("Enter subject name (or type 'done' to finish: )")
                if subject.lower() == "done":
                    break
                try:
                    grade = float(f"Enter grade for {subject}: ")
                    students[name].add_grade(subject,grade)
                except ValueError:
                    print("Invalid grade. Please enter a number.")
            print("All grades added succesfully")
        else:
            print("Student not found")

    if choice == "3":
        name = input("Enter student name: ")
        if name in students:
            stu = students[name]
            stu.show_details()
        else:
            print("Student not found!")

    if choice == "4":
        print("Thanks for visiting.")
        break 
        











































