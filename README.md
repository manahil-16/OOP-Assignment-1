#include <iostream>
#include <fstream>
#include <string>
using namespace std;
class BankAccount {
private:
    string accountNumber;
    string accountHolderName;
    double balance;
public:
    BankAccount(string accNum, string accHolder, double bal) {
    accountNumber = accNum;
    accountHolderName = accHolder;
    balance = bal;
    }
    void deposit(double amount) {
    balance += amount;
    cout << "Amount deposited successfully." << endl;
    }
    void withdraw(double amount) {
    if (amount <= balance) { 
    balance -= amount;
    cout << "Amount withdrawn successfully: " << amount << endl;
        }
    else {
    cout << "Insufficient balance,So amount cannot withdraw." << endl;
        }
    }
    void checkBalance() {
    cout << "Current balance: " << balance << endl;
    }
    
    void saveToFile() const {
    ofstream outFile("accountinfo.txt", ios::app);
    if (outFile.is_open()) {
    outFile << "Account Holder: " << accountHolderName << endl;
    outFile << "Account Number: " << accountNumber << endl;
    outFile << "Balance: " << balance << endl;
    outFile.close();
    cout << "Account information saved to file." << endl;
        }
    else {
    cout << "Error saving to file." << endl;
        }
    }
};
int main() {
    BankAccount account1("1234 987 654", "Mike", 800000);
    BankAccount account2("654 987 1234", "Marcus", 600000);
    BankAccount account3("987 1234 654", "Luna", 160000);
    account1.deposit(2000);
    account1.checkBalance();
    account1.withdraw(1400);
    account1.checkBalance();
    account2.deposit(5000);
    account2.checkBalance();
    account2.withdraw(800000);
    account2.checkBalance();
    account3.deposit(9000);
    account3.checkBalance();
    account3.withdraw(500);
    account3.checkBalance();
    account1.saveToFile();
    account2.saveToFile();
    account3.saveToFile();
    return 0;
}

