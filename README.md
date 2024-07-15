# SmartContractProject

This Solidity program is about depositing and withdrawing tokens. The purpose of this program is to help understand the statements require(), revert(), and assert().

## Description

This program is a Solidity-based smart contract designed to help developers understand and utilize the require(), revert(), and assert() statements for error handling in Solidity. It includes functions to deposit and withdraw tokens, showcasing how these statements can be used to enforce conditions, revert transactions, and ensure correctness in smart contract operations. This contract serves as a foundational example for developers looking to grasp the basic error handling mechanisms in Solidity, providing a stepping stone for more advanced smart contract development.

## Getting Started

### Creating the program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., myBank.sol). Copy and paste the following code into the file:
```javascript
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract TokenBank {
    mapping(address => uint) public balances;

    // Custom error for insufficient balance
    error InsufficientBalance(uint requested, uint available);

    // Function to deposit tokens to the bank account
    function deposit(address _address, uint _amount) public {
        require(_amount > 0, "Deposit amount must be greater than 0");
        balances[_address] += _amount;

        // Assert that the balance is correctly updated
        assert(balances[_address] >= _amount);
    }

    // Function to withdraw tokens from the bank account
    function withdraw(address _address, uint _amount) public {
        if (_amount > balances[_address]) {
            revert InsufficientBalance({requested: _amount, available: balances[_address]});
        }
        balances[_address] -= _amount;
    }
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile myToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "TokenBank" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can scroll down to see the deployed contract in the "Deployed/Unpinned Contracts" section. 

### Executing the program

To deposit tokens, click on the "TokenBank" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "deposit" function. Next, input the address of an account in the _address textfield and the amount of tokens to deposit in the _amount textfield. Finally, click on the "transact" button to execute the function and deposit tokens to the account that was inputted.

To withdraw tokens, click on the "TokenBank" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "withdraw" function. Next, input the address of an account in the _address textfield and the amount of tokens to withdraw in the _amount textfield. Finally, click on the "transact" button to execute the function and withdraw tokens from the account that was inputted.

To check the balance or amount of tokens that an account has, click on the "TokenBank" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "balances" function. Next, input the address of an account in the address textfield. Finally, click on the "call" button to execute the function and the amount of tokens of the account that was inputted will be displayed.

## Authors

Metacrafter napjoquino

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
