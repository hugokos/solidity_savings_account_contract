# solidity_savings_account_contract
Solidity smart contract for an automated joint savings account
# pychain_ledger
Python blockchain ledger system with streamlit web interface

## Technologies

Project uses:

[Solidity](https://docs.soliditylang.org/en/v0.8.14/)

[Remix IDE](https://remix-project.org/)

---

## Installation Guide

# Complete the following steps:

Launch solidity code in Remix IDE to deploy and run transactions on the blockchain




---

## Usage

Utilise Remix to interact with the smart contract. You can set accounts for the joint savings account and utilize the deposit and withdrawl smart contract. See example screenshots below:

!['Set Accounts Function'](https://github.com/hugokos/solidity_savings_account_contract/blob/master/Execution_Results/setAccounts_function.png)

!['Deposit Function'](https://github.com/hugokos/solidity_savings_account_contract/blob/master/Execution_Results/deposit_function.png)

!['Withdraw Function'](https://github.com/hugokos/solidity_savings_account_contract/blob/master/Execution_Results/withdraw_function.png)


**Sample Code:**
```
    Define a function named **withdraw** that will accept two arguments.
    - A `uint` variable named `amount`
    - A `payable address` named `recipient`
    */
    function withdraw(uint amount, address payable recipient) public {

        /*
        Define a `require` statement that checks if the `recipient` is equal to either `accountOne` or `accountTwo`. The `requiere` statement returns the text `"You don't own this account!"` if it does not.
        */
        require(recipient == accountOne || recipient == accountTwo, "You don't own this account");

        /*
        Define a `require` statement that checks if the `balance` is sufficient to accomplish the withdraw operation. If there are insufficient funds, the text `Insufficient funds!` is returned.
        */
        require(contractBalance>=amount, "Insufficient funds!");

        /*
        Add and `if` statement to check if the `lastToWithdraw` is not equal to (`!=`) to `recipient` If `lastToWithdraw` is not equal, then set it to the current value of `recipient`.
        */
        if (lastToWithdraw != recipient) {
            lastToWithdraw=  recipient;
        }

        // Call the `transfer` function of the `recipient` and pass it the `amount` to transfer as an argument.
        recipient.transfer(amount);

        // Set  `lastWithdrawAmount` equal to `amount`
        lastWithdrawAmount=amount;

        // Call the `contractBalance` variable and set it equal to the balance of the contract by using `address(this).balance` to reflect the new balance of the contract.
        contractBalance=address(this).balance;
    }
```

**Screen Shots from Ganache**


---

## Contributors

Hugo Kostelni

---

## License

Open Source
'