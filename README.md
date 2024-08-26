## SMS-FOR-2300214
SMS CODE IN PYTHON WEEK 2 
STUDENT MANAGEMENT SYSTEM
The Student Management System is a Python program that allows you to manage student records. You can add new students, update their information, delete students, and view all students in the system.

 ## Prerequisites
Make sure you have Python installed on your system. You can download it from the official Python website.

## Getting Started
Clone or download this repository to your local machine.
Open a terminal or command prompt and navigate to the project directory.
## Usage
Run the main.py file to start the Student Management System.
Follow the on-screen menu to perform various actions:
Enter 1 to add a new student.
Enter 2 to update student information.
Enter 3 to delete a student.
Enter 4 to view all students.
Enter 5 to exit the system.

## The Code
### student_management_system.py

```python
class Student:
    def _init_(self, student_id, name, age, major):
        self._id = student_id
        self._name = name
        self._age = age
        self._major = major

    @property
    def id(self):
        return self._id

    @property
    def name(self):
        return self._name

    @property
    def age(self):
        return self._age

    @property
    def major(self):
        return self._major

    @name.setter
    def name(self, new_name):
        self._name = new_name

    @age.setter
    def age(self, new_age):
        self._age = new_age

    @major.setter
    def major(self, new_major):
        self._major = new_major


class StudentDatabase:
    def _init_(self):
        self._students = []

    def add_student(self, student):
        self._students.append(student)

    def remove_student(self, student_id):
        self._students = [s for s in self._students if s.id != student_id]

    def get_student_by_id(self, student_id):
        for student in self._students:
            if student.id == student_id:
                return student
        return None

    def get_all_students(self):
        return self._students


class StudentManagementSystem:
    def _init_(self):
        self._database = StudentDatabase()

    def add_new_student(self, student_id, name, age, major):
        student = Student(student_id, name, age, major)
        self._database.add_student(student)

    def delete_student(self, student_id):
        self._database.remove_student(student_id)

    def update_student_info(self, student_id, name=None, age=None, major=None):
        student = self._database.get_student_by_id(student_id)
        if student:
            if name:
                student.name = name
            if age:
                student.age = age
            if major:
                student.major = major

    def get_all_students(self):
        return self._database.get_all_students()

    def display_menu(self):
        print("Student Management System Menu:")
        print("1. Add Student")
        print("2. Update Student Info")
        print("3. Delete Student")
        print("4. Show All Students")
        print("5. Exit")

    def run(self):
        while True:
            self.display_menu()
            choice = input("Enter your choice: ")
            if choice == "1":
                student_id = int(input("Enter student ID: "))
                name = input("Enter student name: ")
                age = int(input("Enter student age: "))
                major = input("Enter student major: ")
                self.add_new_student(student_id, name, age, major)
            elif choice == "2":
                student_id = int(input("Enter student ID: "))
                name = input("Enter updated name (leave empty to skip): ")
                age = int(input("Enter updated age (leave empty to skip): "))
                major = input("Enter updated major (leave empty to skip): ")
                self.update_student_info(student_id, name, age, major)
            elif choice == "3":
                student_id = int(input("Enter student ID to delete: "))
                self.delete_student(student_id)
            elif choice == "4":
                all_students = self.get_all_students()
                for student in all_students:
                    print(f"ID: {student.id}, Name: {student.name}, Age: {student.age}, Major: {student.major}")
            elif choice == "5":
                print("Exiting Student Management System. Goodbye!")
                break
            else:
                print("Invalid choice. Please select a valid option.")

# Example Usage
if _name_ == "_main_":
    system = StudentManagementSystem()
    system.run()
