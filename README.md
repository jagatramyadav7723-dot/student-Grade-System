
import tkinter as tk
from time import strftime
import messagebox

def time_update():
    # Samay ka format set karne ke liye
    string_time = strftime('%H:%M:%S %p')
    lbl_clock.config(text=string_time)
    lbl_clock.after(1000, time_update)

def set_reminder():
    reminder_text = entry_reminder.get()
    if reminder_text:
        messagebox.showinfo("Reminder Set", f"Aapka task set ho gaya hai: {reminder_text}")
    else:
        messagebox.showwarning("Warning", "Kripya pehle koi task likhein!")

# GUI Window Setup
root = tk.Tk()
root.title("Smart Digital Clock & Tasks")
root.geometry("400x250")
root.configure(bg="#2c3e50")

# Clock Label
lbl_clock = tk.Label(root, font=('calibri', 40, 'bold'), background='#2c3e50', foreground='#1abc9c')
lbl_clock.pack(anchor='center', pady=20)

# Reminder Entry
entry_reminder = tk.Entry(root, font=('calibri', 14), width=25)
entry_reminder.pack(pady=10)
entry_reminder.insert(0, "Apna aaj ka task yahan likhein...")

# Button
btn_set = tk.Button(root, text="Task Save Karein", font=('calibri', 12, 'bold'), bg='#1abc9c', fg='white', command=set_reminder)
btn_set.pack(pady=5)

# Clock Function Call
time_update()

# Loop start
root.mainloop()
