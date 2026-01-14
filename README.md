#include <iostream>
#include <vector>
#include <string>
using namespace std;

// Structure to store task details
struct Task {
    string description;
    bool completed;
};

// Function to add a task
void addTask(vector<Task> &tasks) {
    Task t;
    cout << "Enter task: ";
    cin.ignore();
    getline(cin, t.description);
    t.completed = false;
    tasks.push_back(t);
    cout << "Task added successfully!\n";
}

// Function to view all tasks
void viewTasks(const vector<Task> &tasks) {
    if (tasks.empty()) {
        cout << "No tasks available.\n";
        return;
    }

    cout << "\nTo-Do List:\n";
    for (int i = 0; i < tasks.size(); i++) {
        cout << i + 1 << ". " << tasks[i].description
             << " [" << (tasks[i].completed ? "Completed" : "Pending") << "]\n";
    }
}

// Function to mark a task as completed
void markTaskCompleted(vector<Task> &tasks) {
    int taskNo;
    viewTasks(tasks);

    cout << "Enter task number to mark as completed: ";
    cin >> taskNo;

    if (taskNo > 0 && taskNo <= tasks.size()) {
        tasks[taskNo - 1].completed = true;
        cout << "Task marked as completed!\n";
    } else {
        cout << "Invalid task number!\n";
    }
}

// Function to remove a task
void removeTask(vector<Task> &tasks) {
    int taskNo;
    viewTasks(tasks);

    cout << "Enter task number to remove: ";
    cin >> taskNo;

    if (taskNo > 0 && taskNo <= tasks.size()) {
        tasks.erase(tasks.begin() + taskNo - 1);
        cout << "Task removed successfully!\n";
    } else {
        cout << "Invalid task number!\n";
    }
}

int main() {
    vector<Task> tasks;
    int choice;

    do {
        cout << "\n--- To-Do List Manager ---\n";
        cout << "1. Add Task\n";
        cout << "2. View Tasks\n";
        cout << "3. Mark Task as Completed\n";
        cout << "4. Remove Task\n";
        cout << "5. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                addTask(tasks);
                break;
            case 2:
                viewTasks(tasks);
                break;
            case 3:
                markTaskCompleted(tasks);
                break;
            case 4:
                removeTask(tasks);
                break;
            case 5:
                cout << "Exiting program. Goodbye!\n";
                break;
            default:
                cout << "Invalid choice! Try again.\n";
        }
    } while (choice != 5);

    return 0;
}
