import csv

balance = 0
name = ""

# Create Excel-compatible CSV file
file = open("ATM.csv", "w", newline="")
writer = csv.writer(file)
writer.writerow(["Transaction", "Amount", "Balance"])


def menu():
    print("\n===== ATM SYSTEM =====")
    print("1. Create Account")
    print("2. Deposit Money")
    print("3. Withdraw Money")
    print("4. Show Balance")
    print("5. Exit")


while True:

    menu()

    ch = int(input("Enter your choice: "))

    if ch == 1:
        name = input("Enter your name: ")
        balance = float(input("Enter initial balance: "))

        print("Account Created Successfully")
        writer.writerow(["Account Created", balance, balance])

    elif ch == 2:
        amount = float(input("Enter deposit amount: "))
        balance = balance + amount

        print("Money Deposited")
        print("Balance =", balance)

        writer.writerow(["Deposit (+)", amount, balance])

    elif ch == 3:
        amount = float(input("Enter withdraw amount: "))

        if amount <= balance:
            balance = balance - amount

            print("Money Withdrawn")
            print("Balance =", balance)

            writer.writerow(["Withdraw (-)", -amount, balance])
        else:
            print("Insufficient Balance")

    elif ch == 4:
        print("Account Holder:", name)
        print("Current Balance =", balance)

    elif ch == 5:
        print("Thank You!")
        file.close()
        break

    else:
        print("Invalid Choice")
