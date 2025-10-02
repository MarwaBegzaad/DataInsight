# DataInsight
Python project for automated data analysis, visualization, and reporting-showcasing real-world skills.
import tkinter as tk
from tkinter import messagebox

# Function to add a new task
def add_task():
    task = task_entry.get()
    if task:
        task_frame = tk.Frame(tasks_frame, bg='#ffe4e1')
        var = tk.BooleanVar()
        check = tk.Checkbutton(task_frame, variable=var, bg='#ffe4e1')
        check.pack(side=tk.LEFT)
        task_label = tk.Label(task_frame, text=task, bg='#ffe4e1', font=('Helvetica', 12))
        task_label.pack(side=tk.LEFT, padx=5)
        task_frame.pack(fill=tk.X, pady=2)
        task_entry.delete(0, tk.END)
    else:
        messagebox.showwarning("Input Error", "Please enter a task.")

# Function to save daily reflection
def save_reflection():
    reflection = reflection_text.get("1.0", tk.END).strip()
    if reflection:
        messagebox.showinfo("Reflection Saved", "Your reflection has been saved!")
        reflection_text.delete("1.0", tk.END)
    else:
        messagebox.showwarning("Input Error", "Please enter your reflection.")

# Main app window
root = tk.Tk()
root.title("Cute To-Do List")

# Set the background color
root.configure(bg='#ffe4e1')

# Header
header_label = tk.Label(root, text="My To-Do List", bg='#ffe4e1', font=('Helvetica', 16, 'bold'))
header_label.pack(pady=10)

# Task entry and add button
task_frame = tk.Frame(root, bg='#ffe4e1')
task_frame.pack(pady=5)

task_entry = tk.Entry(task_frame, width=40, font=('Helvetica', 12))
task_entry.pack(side=tk.LEFT, padx=5)

add_button = tk.Button(task_frame, text="Add Task", command=add_task, bg='#ffb6c1', font=('Helvetica', 10, 'bold'))
add_button.pack(side=tk.LEFT, padx=5)

# Frame for tasks
tasks_frame = tk.Frame(root, bg='#ffe4e1')
tasks_frame.pack(pady=10, fill=tk.BOTH, expand=True)

# Daily reflection section
reflection_label = tk.Label(root, text="How was your day?", bg='#ffe4e1', font=('Helvetica', 14, 'italic'))
reflection_label.pack(pady=5)

reflection_text = tk.Text(root, height=5, width=50, font=('Helvetica', 12), bg='white', fg='black')
reflection_text.pack(pady=5)

# Save button for reflection
save_button = tk.Button(root, text="Save Reflection", command=save_reflection, bg='#ffb6c1', font=('Helvetica', 10, 'bold'))
save_button.pack(pady=5)

root.mainloop()