# @Version  : 1.0
# @Author   : NGCHEESENG AIT2402008
# @File     : AIT2402008.py

class BankAccount:
    """
    :param account_number: The account number of the bank account.
    :param owner_name: The owner name of the BankAccount.
    :param balance: The balance of the BankAccount.
    :param transactionList: The List of transaction of the account.
    """

    __accountNumber = None
    __owner_name = None
    __balance = None
    __transactionList = None

    def __init__(self, account_number, owner_name, balance=0):
        self.__accountNumber = account_number
        self.__ownerName = owner_name
        self.__balance = balance
        self.__transactionList = []

    # function that let user deposit amount into the balance of bankAccount
    def deposit(self, amount):
        self.__balance += amount
        # adding a list into the transaction list
        self.__transactionList.append([(len(self.__transactionList) + 1), "Deposit", amount])

    # function that let user withdraw amount from the balance of bankAccount
    def withdraw(self, amount):
        self.__balance -= amount
        # adding a list into the transaction list
        self.__transactionList.append([(len(self.__transactionList) + 1), "Withdraw", amount])

    # show the balance of the bankAccount to the user
    def check_balance(self):
        print(f"Account {self.__accountNumber} has balance of RM{self.__balance}")

    # show the bankAccount's transaction list to the user
    def printHistory(self):
        print("Transactions list: ", end="")
        print("[", end="")
        # iterate the self.__transactionList and print out the information list
        for transaction in self.__transactionList:
            if 0 < len(self.__transactionList) != transaction[0]:
                print(transaction, end=",")
            else:
                print(transaction, end="")
        print("]", end="")
        print()

    # function that transfer amount to another bankAccount
    def transfer(self, amount, account):
        # the balance needed to be greater than the amount
        if 0 < self.__balance and amount < self.__balance:
            self.__balance -= amount
            account.receive_transaction(amount)
            self.__transactionList.append([(len(self.__transactionList) + 1), "Transfer(OUT)", amount])
            print(f"You have transferred RM{amount} to account {account.getAccountNumber()}.")
        else:
            print("Insufficient funds")

    def receive_transaction(self, amount):
        self.__balance += amount
        self.__transactionList.append([len(self.__transactionList) + 1, "Transfer(IN)", amount])

    # getter to get bankAccount's account_number
    def getAccountNumber(self):
        return self.__accountNumber

    # getter to get bankAccount's owner_name
    def getOwnerName(self):
        return self.__ownerName


def main():
    loop_main = True  # loop variable for main menu
    loop_account_menu = True  # loop variable for the account menu
    account_using = None  # variable to show which bankAccount is the user using

    accounts = []  # list used to store multiple accounts
    account1 = BankAccount(11122, "Chua", 3000)
    account2 = BankAccount(11124, "Ming", 5000)
    account3 = BankAccount(11126, "Ching", 7000)
    # adding account1, account2, account3 into the accounts list
    accounts.append(account1)
    accounts.append(account2)
    accounts.append(account3)

    # continue showing the main menu
    while loop_main:
        # loop for user to choose account
        while loop_account_menu:
            print("=================Accounts Menu========================")
            for account in accounts:
                print(f"Account Number: {account.getAccountNumber()}, Owner Name: {account.getOwnerName()}")
            print("Please enter the account number to use it!")
            accounts_decision = int(input())
            # a switch statement that compare with cases, if default(_) then ask user to input again.
            match accounts_decision:
                case 11122:
                    account_using = account1
                    loop_account_menu = False
                    print(f"You have logged in {account_using.getAccountNumber()}!")
                case 11124:
                    account_using = account2
                    loop_account_menu = False
                    print(f"You have logged in {account_using.getAccountNumber()}!")
                case 11126:
                    account_using = account3
                    loop_account_menu = False
                    print(f"You have logged in {account_using.getAccountNumber()}!")
                case _:  # default statement
                    print("Please enter the correct account number to use it!")
            print("=====================================================\n")

        # print out main menu
        print("\n=====================================================")
        print("1- Deposit to the account.")
        print("2- Withdraw from the account.")
        print("3- Transfer from the account.")
        print("4- Check balance.")
        print("5- Print transaction history.")
        print("6- Go to the main menu (To choose another account).")
        print("7- Exit (To exit from the program)")
        print("=====================================================")
        # get user input and compare with numbers 1 to 7
        decision = input("Enter your choice: ")
        match decision:
            case "1":  # user deposit page
                print(f"Please enter amount to deposit to {account_using.getAccountNumber()}!")
                amount_deposit = int(input())
                if amount_deposit < 0:
                    print("Please enter a positive amount!")
                    continue
                account_using.deposit(amount_deposit)
                print(f"You have done deposit RM{amount_deposit} into account {account_using.getAccountNumber()}")
                print("=====================================================")
            case "2":  # user withdrawal page
                print(f"Please enter amount to withdraw from {account_using.getAccountNumber()}!")
                amount_withdraw = int(input())
                if amount_withdraw < 0:
                    print("Please enter a positive amount!")
                    continue
                account_using.withdraw(amount_withdraw)
                print(f"You have done withdrawal RM{amount_withdraw} from account {account_using.getAccountNumber()}")
                print("=====================================================")
            case "3":  # user transfer page
                print("Please enter amount to transfer!")
                amount_transfer = int(input())
                if amount_transfer < 0:
                    print("Please enter a positive amount!")
                    continue
                print("Please enter account number to transfer!")
                account_temp = int(input())
                account_to_transfer = None
                for account in accounts:
                    if account_temp == account.getAccountNumber():
                        account_to_transfer = account
                if account_to_transfer is not None:
                    account_using.transfer(amount_transfer, account_to_transfer)
                else:
                    print("The account number is invalid!")
                    continue
                print("=====================================================")
            case "4":  # check private variable __balance of current bankAccount instance page
                account_using.check_balance()
                print("=====================================================")
            case "5":  # check private variable __transaction_list of current bankAccount instance page
                account_using.printHistory()
                print("=====================================================")
            case "6":  # goes to the account menu page, for choosing different account
                loop_account_menu = True
                print()
            case "7":  # exit the main loop
                loop_main = False
                print("Thank for using this program!")
                print("=====================================================")
            case _:  # default input
                print("Invalid input entered!")


if __name__ == '__main__':
    # call main() function
    main()
