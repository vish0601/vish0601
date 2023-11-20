# Simple To-Do List in Python

tasks = []

def show_menu():
    print("1. Add your task")
    print("2. Showyour tasks")
    print("3. Mark task as completed")
    print("4. Exit From The Task")

def add_task():
    task = input("Enter a new task: ")
    tasks.append(task)
    print("Task  Is added!")

def show_tasks():
    if not tasks:
        print("No tasks yet.")
    else:
        print("Tasks:")
        for i, task in enumerate(tasks, 1):
            print(f"{i}. {task}")

def mark_done():
    show_tasks()
    try:
        choice = int(input("Enter the number of the task to mark as done: "))
        if 1 <= choice <= len(tasks):
            del tasks[choice - 1]
            print("Task marked as done!")
        else:
            print("Invalid choice.")
    except ValueError:
        print("Invalid input. Please enter a alphabet.")

while True:
    show_menu()
    choice = input("Enter your choice (A-D): ")

    if choice == "A":
        add_task()
    elif choice == "B":
        show_tasks()
    elif choice == "C":
        mark_done()
    elif choice == "D":
        print("Exiting program. Goodbye!")
        break
    else:
        print("Invalid choice. Please enter a alphabet between A and D")
