# Making a Finance Tracker (using Kali Linux as platform)

## Description of the code

### The Finance Tracker
The Finance Tracker is a simple C++ program designed to help you manage your personal finances. It runs on Kali Linux and provides a straightforward way to track your income and expenses.

### Features :
- **View Transactions**: You can view a list of all your past transactions, including their descriptions, amounts, and whether they are income or expenses.
- **Add Transaction**: You can add new transactions to your finance tracker. Simply provide a description, amount, and specify whether it's an income or expense.
- **Show Total Balance**: The program calculates and displays your total balance, which is the sum of all your income minus your expenses.
- **Save Transactions to File**: Your transaction history can be saved to a file for future reference. This allows you to keep track of your finances across different sessions.
- **User-Friendly Interface**: The program provides a simple menu-based interface, making it easy to navigate and use, even for beginners.



## The Code

```C++
#include <iostream>
#include <fstream>
#include <vector>
#include <string>
#include <sstream>
using namespace std;

// Structure to represent a financial transaction
struct Transaction {
    string description;
    double amount;
    bool isIncome;

    Transaction(string desc, double amt, bool income) : description(desc), amount(amt), isIncome(income) {}
};

// Function to display a transaction
void displayTransaction(const Transaction& transaction) {
    cout << "Description: " << transaction.description << endl;
    cout << "Amount: $" << transaction.amount << endl;
    cout << "Type: " << (transaction.isIncome ? "Income" : "Expense") << endl;
}

// Function to display all transactions
void displayTransactions(const vector<Transaction>& transactions) {
    cout << "Transaction History:" << endl;
    for (const auto& transaction : transactions) {
        displayTransaction(transaction);
        cout << endl;
    }
}

// Function to calculate total balance
double calculateBalance(const vector<Transaction>& transactions) {
    double balance = 0;
    for (const auto& transaction : transactions) {
        balance += (transaction.isIncome ? transaction.amount : -transaction.amount);
    }
    return balance;
}

// Function to add a new transaction
void addTransaction(vector<Transaction>& transactions) {
    string description;
    double amount;
    char type;

    cout << "Enter transaction description: ";
    getline(cin >> ws, description); // Fixed to ensure getline reads correctly after cin

    cout << "Enter transaction amount: $";
    cin >> amount;

    cout << "Is it an income (I) or expense (E)? ";
    cin >> type;
    bool isIncome = (type == 'I' || type == 'i');

    transactions.push_back(Transaction(description, amount, isIncome));
    cout << "Transaction added successfully." << endl;
}

// Function to save transactions to a file
void saveTransactionsToFile(const vector<Transaction>& transactions) {
    ofstream outFile("transactions.txt");
    if (outFile.is_open()) {
        for (const auto& transaction : transactions) {
            outFile << transaction.description << ',' << transaction.amount << ',' << (transaction.isIncome ? 'I' : 'E') << endl;
        }
        outFile.close();
        cout << "Transactions saved to file." << endl;
    } else {
        cerr << "Error: Unable to save transactions to file." << endl;
    }
}

// Function to load transactions from a file
void loadTransactionsFromFile(vector<Transaction>& transactions) {
    ifstream inFile("transactions.txt");
    if (inFile.is_open()) {
        string line;
        while (getline(inFile, line)) {
            string description;
            double amount;
            char type;
            istringstream ss(line);
            getline(ss, description, ',');
            ss >> amount;
            ss.ignore();
            ss >> type;
            bool isIncome = (type == 'I' || type == 'i');
            transactions.push_back(Transaction(description, amount, isIncome));
        }
        inFile.close();
        cout << "Transactions loaded from file." << endl;
    } else {
        cerr << "File not found or unable to open. Starting with an empty transaction list." << endl;
    }
}

int main() {
    vector<Transaction> transactions;

    // Load transactions from file
    loadTransactionsFromFile(transactions);

    int choice;
    do {
        cout << "Personal Finance Tracker" << endl;
        cout << "1. View Transactions" << endl;
        cout << "2. Add Transaction" << endl;
        cout << "3. Show Total Balance" << endl;
        cout << "4. Save Transactions to File" << endl;
        cout << "5. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                displayTransactions(transactions);
                cout << endl;
                break;
            case 2:
                addTransaction(transactions);
                cout << endl;
                break;
            case 3:
                cout << "Total Balance: $" << calculateBalance(transactions) << endl;
                cout << endl;
                break;
            case 4:
                saveTransactionsToFile(transactions);
                cout << endl;
                break;
            case 5:
                cout << "Exiting..." << endl;
                break;
            default:
                cout << "Invalid choice. Please try again." << endl;
        }
    } while (choice != 5);

    return 0;
}

```

## Output

Step 1 : Open Kali Linux terminal

Step 2 : Write the following Commands


![image](https://github.com/Shantanu2911/Sem-2-Practical/assets/143939657/143a983d-4865-4fba-a23a-a233ebd32658)

![image](https://github.com/Shantanu2911/Sem-2-Practical/assets/143939657/085e3f4e-4dc9-4a9a-96bd-61dba2829951)

![image](https://github.com/Shantanu2911/Sem-2-Practical/assets/143939657/9067a218-e6cb-4a1b-b009-d24dc4f3b816)

## The Final Output 

![image](https://github.com/Shantanu2911/Sem-2-Practical/assets/143939657/6c69ac49-d25c-455e-951f-ae3568bf4f2d)

