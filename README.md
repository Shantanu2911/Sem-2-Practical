# Personal Finance Tracker (Using Kali Linux as a platform)

## Overview

This program is a simple personal finance tracker implemented in C++. It allows users to manage their financial transactions, including viewing transactions, adding new transactions, calculating the total balance, and saving transactions to a file.

## Features

- View Transactions: Display a list of all recorded transactions.
- Add Transaction: Add a new transaction with a description, amount, and type (income or expense).
- Show Total Balance: Calculate and display the total balance based on the recorded transactions.
- Save Transactions to File: Save all recorded transactions to a file named "transactions.txt".
- Exit: Exit the program.

## Usage

1. Run the program.
2. Select options from the menu to manage transactions.
3. Follow the prompts to add new transactions or view the total balance.
4. Save transactions to a file if desired.
5. Exit the program when done.

## Code Structure

The code is structured as follows:

- `main()`: The entry point of the program. It contains the main control flow, menu display, and option handling.
- Functions:
  - `displayTransaction(const Transaction& transaction)`: Display details of a single transaction.
  - `displayTransactions(const vector<Transaction>& transactions)`: Display a list of all transactions.
  - `calculateBalance(const vector<Transaction>& transactions)`: Calculate the total balance based on transactions.
  - `addTransaction(vector<Transaction>& transactions)`: Add a new transaction to the list.
  - `saveTransactionsToFile(const vector<Transaction>& transactions)`: Save transactions to a file.
  - `loadTransactionsFromFile(vector<Transaction>& transactions)`: Load transactions from a file.

## File Handling

- Transactions are stored in a vector of `Transaction` objects.
- Transactions are saved to and loaded from a file named "transactions.txt".
- Each transaction is stored in a comma-separated format: description, amount, type (I for income, E for expense).

## Dependencies

- C++ standard library:
  - iostream: Input and output operations.
  - fstream: File input and output operations.
  - vector: Dynamic array container.
  - string: String manipulation operations.
  - sstream: String stream processing.

## Compilation

Compile the code using a C++ compiler such as g++:


## Output

Step 1 : Open Kali Linux terminal

Step 2 : Write the following Commands


![image](https://github.com/Shantanu2911/Sem-2-Practical/assets/143939657/143a983d-4865-4fba-a23a-a233ebd32658)

![image](https://github.com/Shantanu2911/Sem-2-Practical/assets/143939657/085e3f4e-4dc9-4a9a-96bd-61dba2829951)

![image](https://github.com/Shantanu2911/Sem-2-Practical/assets/143939657/9067a218-e6cb-4a1b-b009-d24dc4f3b816)

## The Final Output 

![image](https://github.com/Shantanu2911/Sem-2-Practical/assets/143939657/6c69ac49-d25c-455e-951f-ae3568bf4f2d)
