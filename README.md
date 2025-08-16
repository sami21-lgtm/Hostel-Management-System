# Hostel-Management-System
import sys

hostel_records = {}

def add_student():
    roll = input("Enter Roll Number: ")
    if roll in hostel_records:
        print("Student already exists!")
        return
    name = input("Enter Name: ")
    room = input("Enter Room Number: ")
    contact = input("Enter Contact Number: ")
    hostel_records[roll] = {
        "name": name,
        "room": room,
        "contact": contact
    }
    print("Student added successfully.\n")

def view_students():
    if not hostel_records:
        print("No records to show.\n")
        return
    print("\nAll Hostel Students:")
    print("-" * 40)
    for roll, data in hostel_records.items():
        print(f"Roll: {roll} | Name: {data['name']} | Room: {data['room']} | Contact: {data['contact']}")
    print("-" * 40, "\n")

def search_student():
    roll = input("Enter Roll Number to Search: ")
    if roll in hostel_records:
        data = hostel_records[roll]
        print(f"Found: Roll: {roll} | Name: {data['name']} | Room: {data['room']} | Contact: {data['contact']}\n")
    else:
        print("Student not found.\n")

def delete_student():
    roll = input("Enter Roll Number to Delete: ")
    if roll in hostel_records:
        del hostel_records[roll]
        print("Student deleted successfully.\n")
    else:
        print("Student not found.\n")

def menu():
    while True:
        print("Hostel Management System")
        print("1. Add Student")
        print("2. View All Students")
        print("3. Search Student")
        print("4. Delete Student")
        print("5. Exit")
        choice = input("Enter your choice (1-5): ")
        if choice == '1':
            add_student()
        elif choice == '2':
            view_students()
        elif choice == '3':
            search_student()
        elif choice == '4':
            delete_student()
        elif choice == '5':
            print("Exiting program. Goodbye!")
            sys.exit()
        else:
            print("Invalid choice. Try again.\n")

if __name__ == "__main__":
    menu()
