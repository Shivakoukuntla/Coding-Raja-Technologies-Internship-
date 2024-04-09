# Coding-Raja-Technologies-Internship- Task -2
import sys
class BudgetTracker:
    def __init__(self, initial_balance):
        self.balance = initial_balance
        self.transactions = []

    def deposit(self, amount, description):
        self.balance += amount
        self.transactions.append((amount, description))

    def withdraw(self, amount, description):
        if amount <= self.balance:
            self.balance -= amount
            self.transactions.append((-amount, description))
        else:
            print("Insufficient funds!")

    def show_balance(self):
        print(f"Current balance: {self.balance}")

    def show_transactions(self):
        print("Transaction history:")
        for transaction in self.transactions:
            amount, description = transaction
            if amount > 0:
                print(f"Deposit: {amount} - {description}")
            else:
                print(f"Withdrawal: {-amount} - {description}")


def main():
    initial_balance = float(input("Enter initial balance: "))
    tracker = BudgetTracker(initial_balance)

    while True:
        print("\n1. Deposit")
        print("2. Withdraw")
        print("3. Show balance")
        print("4. Show transaction history")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            amount = float(input("Enter deposit amount: "))
            description = input("Enter description: ")
            tracker.deposit(amount, description)
        elif choice == '2':
            amount = float(input("Enter withdrawal amount: "))
            description = input("Enter description: ")
            tracker.withdraw(amount, description)
        elif choice == '3':
            tracker.show_balance()
        elif choice == '4':
            tracker.show_transactions()
        elif choice == '5':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")


if __name__ == "__main__":
    main()
