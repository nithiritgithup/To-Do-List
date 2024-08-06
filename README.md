---

# Todo List Manager

## Project Overview

The Todo List Manager is a simple console-based application that allows users to manage their tasks. Users can add, view, and delete tasks, and the application can save tasks to a file and load them when the application starts. This project is designed to help beginners practice Python programming concepts such as functions, lists, and file handling.

## Features

- **Add Tasks**: Add new tasks to your todo list.
- **View Tasks**: Display all current tasks.
- **Delete Tasks**: Remove tasks from your list.
- **Save and Exit**: Save the current list of tasks to a file and exit the application.
- **Exit Without Saving**: Exit the application without saving any changes.

## Installation

No special installation is required. This project is compatible with Python 3.x. Ensure Python is installed on your computer.

## Getting Started

### File Structure

Create a directory for your project and navigate into it. Inside the directory, create a Python file named `todo_list_manager.py`.

### Project Code

Save the following code in `todo_list_manager.py`:

```python
# todo_list_manager.py

def display_menu():
    print("\nTodo List Manager")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Delete Task")
    print("4. Save and Exit")
    print("5. Exit Without Saving")

def load_tasks(filename="tasks.txt"):
    try:
        with open(filename, "r") as file:
            tasks = file.readlines()
        return [task.strip() for task in tasks]
    except FileNotFoundError:
        return []

def save_tasks(tasks, filename="tasks.txt"):
    with open(filename, "w") as file:
        for task in tasks:
            file.write(task + "\n")

def add_task(tasks):
    task = input("Enter the task: ")
    tasks.append(task)
    print("Task added.")

def view_tasks(tasks):
    if tasks:
        print("\nYour tasks:")
        for i, task in enumerate(tasks, 1):
            print(f"{i}. {task}")
    else:
        print("No tasks found.")

def delete_task(tasks):
    view_tasks(tasks)
    try:
        task_number = int(input("Enter the task number to delete: "))
        if 1 <= task_number <= len(tasks):
            removed_task = tasks.pop(task_number - 1)
            print(f"Task '{removed_task}' deleted.")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Please enter a valid number.")

def main():
    tasks = load_tasks()
    
    while True:
        display_menu()
        choice = input("Choose an option: ")
        
        if choice == "1":
            add_task(tasks)
        elif choice == "2":
            view_tasks(tasks)
        elif choice == "3":
            delete_task(tasks)
        elif choice == "4":
            save_tasks(tasks)
            print("Tasks saved.")
            break
        elif choice == "5":
            print("Exiting without saving.")
            break
        else:
            print("Invalid choice. Please select a valid option.")

if __name__ == "__main__":
    main()
```

### Running the Project

1. Save the code above in a file named `todo_list_manager.py`.
2. Open a terminal or command prompt.
3. Navigate to the directory where `todo_list_manager.py` is saved.
4. Run the script using Python:
   ```bash
   python todo_list_manager.py
   ```

### Usage

1. **Add Task**: Select option 1 and enter the task you want to add.
2. **View Tasks**: Select option 2 to see all your current tasks.
3. **Delete Task**: Select option 3 to delete a specific task by its number.
4. **Save and Exit**: Select option 4 to save the current tasks to a file and exit the application.
5. **Exit Without Saving**: Select option 5 to exit the application without saving any changes.

## Tips for Enhancement

- **Task Prioritization**: Add functionality to mark tasks as high or low priority.
- **Task Due Dates**: Include due dates for tasks and sort them accordingly.
- **Graphical User Interface**: Use a GUI library like Tkinter to create a more user-friendly interface.

## License

This project is for educational purposes and is provided as-is. Feel free to modify and use it according to your needs.

## Contact

For questions or feedback, you can reach out to:

- **Your Name**: [your.email@example.com]

---
