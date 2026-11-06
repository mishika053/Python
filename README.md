
# Python Lists Mini Project
# Student Marks System

student_names = ["Aman", "Riya", "Kabir"]
student_marks = [78, 92, 65]


while True:
    print("\n===== STUDENT MARKS SYSTEM =====")
    print("1. Show Records")
    print("2. Add Student")
    print("3. Search Student")
    print("4. Update Marks")
    print("5. Show Summary")
    print("6. Sort Marks")
    print("7. Exit")

    choice = input("Enter your choice: ")

    # 1. Show Records
    if choice == "1":
        print("\n--- Student Records ---")

        if len(student_names) == 0:
            print("No records available.")
        else:
            for i in range(len(student_names)):
                print(student_names[i], ":", student_marks[i])

    # 2. Add Student
    elif choice == "2":
        name = input("Enter student name: ").strip()

        if name == "":
            print("Name cannot be blank.")
            continue

        try:
            marks = float(input("Enter marks (0-100): "))

            if marks < 0 or marks > 100:
                print("Marks must be between 0 and 100.")
            else:
                student_names.append(name)
                student_marks.append(marks)
                print("Student added successfully!")

        except ValueError:
            print("Please enter valid numeric marks.")

    # 3. Search Student
    elif choice == "3":
        name = input("Enter student name to search: ").strip()

        if name in student_names:
            index = student_names.index(name)
            print("Name:", student_names[index])
            print("Marks:", student_marks[index])
        else:
            print("Student not found.")

    # 4. Update Marks
    elif choice == "4":
        name = input("Enter student name: ").strip()

        if name in student_names:
            index = student_names.index(name)

            try:
                new_marks = float(input("Enter new marks: "))

                if 0 <= new_marks <= 100:
                    student_marks[index] = new_marks
                    print("Marks updated successfully!")
                else:
                    print("Marks must be between 0 and 100.")

            except ValueError:
                print("Please enter valid numeric marks.")
        else:
            print("Student not found.")

    # 5. Show Summary
    elif choice == "5":
        if len(student_marks) > 0:
            average = sum(student_marks) / len(student_marks)

            print("\n--- Marks Summary ---")
            print("Average Marks:", round(average, 2))
            print("Highest Marks:", max(student_marks))
            print("Lowest Marks:", min(student_marks))
        else:
            print("No marks available.")

    # 6. Sort Marks
    elif choice == "6":
        if len(student_names) > 0:
            records = list(zip(student_names, student_marks))
            records.sort(key=lambda x: x[1], reverse=True)

            print("\n--- Sorted Records ---")

            for name, marks in records:
                print(name, ":", marks)
        else:
            print("No records available.")

    # 7. Exit
    elif choice == "7":
        print("Thank you for using Student Marks System!")
        break

    else:
        print("Invalid choice. Please try again.")
