class PersonalFinanceManager:
    def __init__(self):
        self.expenses = []

    def add_expense(self, description, amount, category):
        expense = {
            "description": description,
            "amount": amount,
            "category": category
        }
        self.expenses.append(expense)
        print(f"Added expense: {description}, Amount: {amount}, Category: {category}")

    def view_expenses(self):
        if not self.expenses:
            print("No expenses recorded.")
            return

        print("Expense History:")
        for i, expense in enumerate(self.expenses, start=1):
            print(f"{i}. {expense['description']} - ${expense['amount']} ({expense['category']})")

    def calculate_total_expenses(self):
        total = sum(expense['amount'] for expense in self.expenses)
        print(f"Total Expenses: ${total}")

    def view_expenses_by_category(self):
        if not self.expenses:
            print("No expenses recorded.")
            return

        category_expenses = {}
        for expense in self.expenses:
            category = expense['category']
            amount = expense['amount']
            if category in category_expenses:
                category_expenses[category] += amount
            else:
                category_expenses[category] = amount

        print("Expenses by Category:")
        for category, total in category_expenses.items():
            print(f"{category}: ${total}")

def main():
    manager = PersonalFinanceManager()
    while True:
        print("\nPersonal Finance Manager")
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. Calculate Total Expenses")
        print("4. View Expenses by Category")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            description = input("Enter description: ")
            amount = float(input("Enter amount: "))
            category = input("Enter category: ")
            manager.add_expense(description, amount, category)
        elif choice == '2':
            manager.view_expenses()
        elif choice == '3':
            manager.calculate_total_expenses()
        elif choice == '4':
            manager.view_expenses_by_category()
        elif choice == '5':
            print("Exiting Personal Finance Manager. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
