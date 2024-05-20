import json
with open("baza.json", "r") as ATM:
    baza = json.load(ATM)
pincode = int(input("write down the pincode: "))
correct_pincode = baza["pincode"]
credit_card_balance = baza["balance"]


def withdraw():
    global credit_card_balance
    money_to_withdraw = int(input("Enter the amount of money you want to withdraw: "))
    if money_to_withdraw > credit_card_balance:
        print("Transaction cannot be completed.")
    else:
        credit_card_balance -= money_to_withdraw
        with open("baza.json", "w") as ATM:
            baza["balance"] = credit_card_balance
            json.dump(baza, ATM)
        print(f"Now your balance is {credit_card_balance}")


def put_money():
    global credit_card_balance
    due_money = int(input("What amount of money do you want to put on your credit card? "))
    credit_card_balance += due_money
    with open("baza.json", "w") as ATM:
        baza["balance"] = credit_card_balance
        json.dump(baza, ATM)
    print(f"Now your balance is {credit_card_balance}")


def check_balance_in_currency():
    global credit_card_balance
    print("Choose the currency to view your balance:")
    print("1. Dollar")
    print("2. Euro")
    print("3. Yuan")
    currency_choice = int(input())
    if currency_choice == 1:
        print(f"Your balance in dollars is: {credit_card_balance // 93}")
    elif currency_choice == 2:
        print(f"Your balance in euros is: {credit_card_balance // 100}")
    elif currency_choice == 3:
        print(f"Your balance in yuan is: {credit_card_balance // 13}")
    else:
        print("Invalid choice")


counter_of_incorrect_passwords = 0

while True:
    if pincode == correct_pincode:
        command = int(input("""1. Withdraw money
2. Put money to the bank account
3. See the balance
4. Check balance in a different currency
5. Exit the menu
    Enter the command: """))
        if command == 1:
            withdraw()
        elif command == 2:
            put_money()
        elif command == 3:
            print(f"Your balance is {credit_card_balance}")
        elif command == 4:
            check_balance_in_currency()
        elif command == 5:
            choice_to_exit = input("Are you sure you want to exit? If no, press no, if yes, press yes: ")
            if choice_to_exit == "yes":
                print("Have a nice day!")
                break
            else:
                continue
        else:
            print("Invalid command")
    else:
        print("Incorrect pincode!")
        counter_of_incorrect_passwords += 1
        if counter_of_incorrect_passwords == 2:
            print("Your card is blocked, please contact the bank!")
            break
        pincode = int(input("write down the pincode: "))
