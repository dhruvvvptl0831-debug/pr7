# Project Overview

This repository contains a Jupyter Notebook that executes the following Python code:

```python
import datetime
import time
import math
import random
import string
import uuid
import os
import importlib


# 🕒 Date & Time Utilities
def datetime_menu():
    while True:
        print("\n--- DateTime Utilities ---")
        print("1. Current Date & Time")
        print("2. Calculate Date Difference")
        print("3. Format Current Date")
        print("4. Stopwatch")
        print("5. Countdown Timer")
        print("6. Back")

        choice = input("Enter your choice: ")

        if choice == '1':
            print("Current Date & Time:", datetime.datetime.now())
        elif choice == '2':
            d1 = input("Enter first date (YYYY-MM-DD): ")
            d2 = input("Enter second date (YYYY-MM-DD): ")
            try:
                date1 = datetime.datetime.strptime(d1, "%Y-%m-%d")
                date2 = datetime.datetime.strptime(d2, "%Y-%m-%d")
                print("Difference:", abs((date2 - date1).days), "days")
            except ValueError:
                print("Invalid date format!")
        elif choice == '3':
            print("Formatted Date:", datetime.datetime.now().strftime("%d-%m-%Y %H:%M:%S"))
        elif choice == '4':
            input("Press Enter to start stopwatch...")
            start = time.time()
            input("Press Enter to stop...")
            end = time.time()
            print("Elapsed Time:", round(end - start, 2), "seconds")
        elif choice == '5':
            sec = int(input("Enter seconds: "))
            for i in range(sec, 0, -1):
                print(i, end=' ', flush=True)
                time.sleep(1)
            print("\nTime’s up!")
        elif choice == '6':
            break
        else:
            print("Invalid choice!")


# 🧮 Math Utilities
def math_menu():
    while True:
        print("\n--- Math Utilities ---")
        print("1. Factorial")
        print("2. Compound Interest")
        print("3. Trigonometric Value")
        print("4. Area of Circle")
        print("5. Back")

        choice = input("Enter your choice: ")

        if choice == '1':
            n = int(input("Enter number: "))
            print("Factorial:", math.factorial(n))
        elif choice == '2':
            p = float(input("Enter Principal: "))
            r = float(input("Enter Rate: "))
            t = float(input("Enter Time (years): "))
            amount = p * (pow((1 + r / 100), t))
            print("Compound Interest:", amount - p)
        elif choice == '3':
            angle = float(input("Enter angle in degrees: "))
            rad = math.radians(angle)
            print(f"sin({angle}) = {math.sin(rad):.2f}")
            print(f"cos({angle}) = {math.cos(rad):.2f}")
            print(f"tan({angle}) = {math.tan(rad):.2f}")
        elif choice == '4':
            r = float(input("Enter radius: "))
            print("Area of Circle:", round(math.pi * r * r, 2))
        elif choice == '5':
            break
        else:
            print("Invalid choice!")


# 🎲 Random Utilities
def random_menu():
    while True:
        print("\n--- Random Utilities ---")
        print("1. Random Number")
        print("2. Random Password")
        print("3. Random OTP")
        print("0. Back")

        choice = input("Enter your choice: ")

        if choice == '1':
            print("Random Number:", random.randint(1, 100))
        elif choice == '2':
            length = int(input("Enter password length: "))
            chars = string.ascii_letters + string.digits + string.punctuation
            print("Password:", ''.join(random.choice(chars) for _ in range(length)))
        elif choice == '3':
            print("OTP:", ''.join(random.choice(string.digits) for _ in range(6)))
        elif choice == '0':
            break
        else:
            print("Invalid choice!")


# 🧾 UUID Generator
def uuid_menu():
    while True:
        print("\n--- UUID Generator ---")
        print("1. Generate UUID4")
        print("0. Back")

        choice = input("Enter your choice: ")
        if choice == '1':
            print("Generated UUID:", uuid.uuid4())
        elif choice == '0':
            break
        else:
            print("Invalid choice!")


# 📂 File Operations
def file_menu():
    while True:
        print("\n--- File Operations ---")
        print("1. Create File")
        print("2. Write to File")
        print("3. Read File")
        print("4. Append to File")
        print("0. Back")

        choice = input("Enter your choice: ")

        if choice == '1':
            name = input("Enter file name: ")
            open(name, 'w').close()
            print("File created successfully.")
        elif choice == '2':
            name = input("Enter file name: ")
            data = input("Enter text: ")
            with open(name, 'w') as f:
                f.write(data)
            print("Written successfully.")
        elif choice == '3':
            name = input("Enter file name: ")
            if os.path.exists(name):
                with open(name, 'r') as f:
                    print("\nFile Content:\n", f.read())
            else:
                print("File not found!")
        elif choice == '4':
            name = input("Enter file name: ")
            data = input("Enter text to append: ")
            with open(name, 'a') as f:
                f.write("\n" + data)
            print("Appended successfully.")
        elif choice == '0':
            break
        else:
            print("Invalid choice!")


# 🔍 Module Explorer
def explorer_menu():
    print("\n--- Module Explorer ---")
    mod = input("Enter module name (e.g., math, datetime): ")
    try:
        module = importlib.import_module(mod)
        print(f"\nAvailable functions and attributes in '{mod}':")
        for item in dir(module):
            print(item)
    except ModuleNotFoundError:
        print("Module not found!")


# 🧠 MAIN MENU
def menu():
    while True:
        print("\n=== Multi Utility Toolkit ===")
        print("1. Date & Time Utilities")
        print("2. Math Utilities")
        print("3. Random Utilities")
        print("4. UUID Generator")
        print("5. File Operations")
        print("6. Explorer Utility")
        print("0. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            datetime_menu()
        elif choice == '2':
            math_menu()
        elif choice == '3':
            random_menu()
        elif choice == '4':
            uuid_menu()
        elif choice == '5':
            file_menu()
        elif choice == '6':
            explorer_menu()
        elif choice == '0':
            print("Exiting... Thank you for using the Toolkit!")
            break
        else:
            print("Invalid choice. Try again.")


# 🚀 Entry Point
if __name__ == "__main__":
    menu()



```

## How to Run
1. Open the notebook file `new 7.ipynb` in Jupyter Notebook or JupyterLab.
2. Run all cells sequentially to reproduce the results.

## Requirements
Ensure you have Python and Jupyter installed. Install required libraries using:
```bash
pip install -r requirements.txt
```

## Output
All outputs and visualizations are generated directly in the notebook cells during execution.