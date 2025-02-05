def show_tasks(todo_list):
    if not todo_list:
        print("Your To-Do List is empty!")
    else:
        print("\Your To-Do List:")
        for task_id, task in todo_list.items():
            print(f"{task_id}. {task}")

def main():
    # Pre-filled tasks for a manager
    todo_list = {
        1: "Schedule a team meeting",
        2: "Review project reports",
        3: "Approve leave requests",
        4: "Conduct team check-ins",
        5: "Set team goals for the quarter"
    }
    task_counter = 6  # Next available task number for new tasks

    while True:
        print("\nOptions:")
        print("1. Create a new task")
        print("2. See all tasks")
        print("3. Update a task")
        print("4. Delete a task")
        print("5. Exit")

        choice = input("Enter your choice (1-5): ")

        match choice:
            case '1':  # Create a new task
                task = input("Enter the task description: ")
                todo_list[task_counter] = task  # Add task to dictionary
                print(f"Task added: {task}")
                task_counter += 1  # Increment task number
            case '2':  # See all tasks
                show_tasks(todo_list)
            case '3':  # Update a task
                show_tasks(todo_list)
                try:
                    task_num = int(input("Enter the task number to update: "))
                    if task_num in todo_list:
                        new_task = input("Enter the updated task description: ")
                        todo_list[task_num] = new_task  # Update the task
                        print(f"Task {task_num} updated to: {new_task}")
                    else:
                        print("Task number not found.")
                except ValueError:
                    print("Please enter a valid number.")
            case '4':  # Delete a task
                show_tasks(todo_list)
                try:
                    task_num = int(input("Enter the task number to delete: "))
                    if task_num in todo_list:
                        removed_task = todo_list.pop(task_num)  # Remove task from dictionary
                        print(f"Task {task_num} deleted: {removed_task}")
                    else:
                        print("Task number not found.")
                except ValueError:
                    print("Please enter a valid number.")
            case '5':  # Exit the program
                print("Goodbye!")
                break
            case _:  # If the input is not 1-5
                print("Invalid choice. Please select a number between 1 and 5.")

if _name_ == "_main_":
    main()