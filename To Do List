import json
import os
from datetime import datetime

class TodoList:
    def __init__(self, filename="todolist.json"):
        self.filename = filename
        self.tasks = self.load_tasks()

    def load_tasks(self):
        if os.path.exists(self.filename):
            with open(self.filename, 'r') as file:
                return json.load(file)
        else:
            return []

    def save_tasks(self):
        with open(self.filename, 'w') as file:
            json.dump(self.tasks, file, indent=2)

    def show_tasks(self):
        if not self.tasks:
            print("No tasks in the to-do list.")
        else:
            print("To-Do List:")
            for index, task in enumerate(self.tasks, start=1):
                print(f"{index}. {task['text']} - {task['date']}")

    def add_task(self, text):
        date = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        task = {"text": text, "date": date}
        self.tasks.append(task)
        self.save_tasks()
        print("Task added successfully.")

    def remove_task(self, index):
        if 1 <= index <= len(self.tasks):
            removed_task = self.tasks.pop(index - 1)
            self.save_tasks()
            print(f"Removed task: {removed_task['text']}")
        else:
            print("Invalid task index.")

# Example usage:
todo_list = TodoList()

while True:
    print("\n1. Show Tasks")
    print("2. Add Task")
    print("3. Remove Task")
    print("4. Quit")

    choice = input("Enter your choice (1-4): ")

    if choice == '1':
        todo_list.show_tasks()
    elif choice == '2':
        task_text = input("Enter the task: ")
        todo_list.add_task(task_text)
    elif choice == '3':
        todo_list.show_tasks()
        task_index = int(input("Enter the task index to remove: "))
        todo_list.remove_task(task_index)
    elif choice == '4':
        print("Exiting the To-Do List application. Goodbye!")
        break
    else:
        print("Invalid choice. Please enter a number between 1 and 4.")
