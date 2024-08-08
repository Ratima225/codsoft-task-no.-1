class TodoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({"task": task, "completed": False})
        print(f"Added task: {task}")

    def update_task(self, task_number, new_task):
        if 0 <= task_number < len(self.tasks):
            self.tasks[task_number]["task"] = new_task
            print(f"Updated task #{task_number + 1} to: {new_task}")
        else:
            print("Invalid task number")

    def complete_task(self, task_number):
        if 0 <= task_number < len(self.tasks):
            self.tasks[task_number]["completed"] = True
            print(f"Marked task #{task_number + 1} as completed")
        else:
            print("Invalid task number")

    def show_tasks(self):
        if not self.tasks:
            print("No tasks in the to-do list.")
        else:
            for index, task in enumerate(self.tasks):
                status = "Done" if task["completed"] else "Pending"
                print(f"{index + 1}. {task['task']} - {status}")

def main():
    todo_list = TodoList()

    while True:
        print("\nTo-Do List Application")
        print("1. Add a task")
        print("2. Update a task")
        print("3. Complete a task")
        print("4. Show tasks")
        print("5. Exit")

        choice = input("Choose an option: ")

        if choice == "1":
            task = input("Enter the task: ")
            todo_list.add_task(task)
        elif choice == "2":
            task_number = int(input("Enter the task number to update: ")) - 1
            new_task = input("Enter the new task: ")
            todo_list.update_task(task_number, new_task)
        elif choice == "3":
            task_number = int(input("Enter the task number to mark as completed: ")) - 1
            todo_list.complete_task(task_number)
        elif choice == "4":
            todo_list.show_tasks()
        elif choice == "5":
            print("Exiting the application.")
            break
        else:
            print("Invalid option. Please choose a valid option.")

if __name__ == "__main__":
    main()
