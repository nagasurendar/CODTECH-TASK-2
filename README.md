# CODTECH-TASK-2class Student:
    def _init_(self, name):
        self.name = name
        self.grades = {}

    def add_grade(self, subject, grade):
        self.grades[subject] = grade

    def calculate_average(self):
        if len(self.grades) == 0:  # Check if there are grades
            return 0
        total = sum(self.grades.values())
        average = total / len(self.grades)
        return average

    def get_letter_grade(self):
        average = self.calculate_average()
        if average >= 90:
            return "A"
        elif average >= 80:
            return "B"
        elif average >= 70:
            return "C"
        elif average >= 60:
            return "D"
        else:
            return "F"

    def display_grades(self):
        print(f"Student Name: {self.name}")
        print("Subject\tGrade")
        for subject, grade in self.grades.items():
            print(f"{subject}\t{grade}")
        average = self.calculate_average()
        print(f"Average Grade: {average:.2f}")
        print(f"Letter Grade: {self.get_letter_grade()}")

# Get user input for student name
student_name = input("Enter student name: ")

# Create a new student object
student = Student(student_name)

# Get user input for grades
while True:
    subject = input("Enter subject (or 'quit' to exit): ")
    if subject.lower() == "quit":
        break
    try:
        grade = float(input("Enter grade: "))
        student.add_grade(subject, grade)
    except ValueError:
        print("Please enter a valid number for the grade.")

# Display student grades and statistics
student.display_grades()
