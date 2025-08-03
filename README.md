# 🧮 Python Command-Line Calculator with History

This is a simple terminal-based calculator built with Python that supports basic arithmetic operations and logs each calculation to a history file.

## 💡 Features
- Perform calculations using `+`, `-`, `*`, `/`
- Prevents division by zero
- View calculation history with `history` command
- Clear history using `clear` command
- Exit the calculator using `exit`

## 🛠️ Tech Stack
- Python 3
- File I/O for history handling
- Basic CLI interaction

## 📂 Project Structure
calculator.py # Main calculator script
history.txt # Stores calculation history
README.md # Project details


## 🚀 How to Run
1. Make sure you have Python installed.
2. Clone the repository or download the files.
3. Run the calculator:
``bash
python calculator.py

📸 Sample Output
<img width="905" height="518" alt="image" src="https://github.com/user-attachments/assets/cea3a9ec-7420-4b30-a960-33fdae7701d0" />


Enter Calculation (+ - * /) or command (history, clear, exit) 5 + 4
Result: 9

Enter Calculation (+ - * /) or command (history, clear, exit) history
5 + 4 = 9


📌 Author
Sharad Jadhav


Code :


```bash

HISTORY_FILE = 'history.txt'

def show_history():
    file = open(HISTORY_FILE,'r')
    lines = file.readlines()
    if len(lines) == 0:
        print("No history found!")
    else:
        for line in reversed(lines):
            print(line.strip())
    file.close() 

def clear_history():
        file = open(HISTORY_FILE,'w')
        file.close()
        print("History cleared.")

def save_to_history(equation,result):
     file = open(HISTORY_FILE,'a')
     file.write(equation + '=' + str(result) + '\n')
     file.close()

def calculate(user_input):
     parts = user_input.split()
     if len(parts) != 3:
          print('Invalid input. use format: number operator number (e.g 8 + 8)')
          return
     
     num1 = float(parts[0])
     op = parts[1]
     num2 = float(parts[2])

     if op == '+':
          result = num1 + num2
     elif op == '-':
          result = num1 - num2
     elif op == '*':
          result = num1 * num2
     elif op == '/':
          if num2 == 0:
               print("Cannot divide by zero")
               return
          result = num1 / num2    
     else:
          print("Invalid Operator. Use only + - * /")
          return
     
     if int(result) == result:
          result = int(result)
     print('Result:',result)
     save_to_history(user_input, result)
    
def main():
     print('---SIMPLE CALCULATOR (type history, clear, exit)')
     while True:
        user_input = input('Enter Calculation (+ - * /) or command (history, clear, exit)')
        if user_input == 'exit':
             print('GOODBYE!')
             break
        elif user_input == 'history':
             show_history()
        elif user_input == 'clear':
             clear_history()
        else:
             calculate(user_input)

main()


