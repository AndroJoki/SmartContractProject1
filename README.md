# SmartContractProject

This Solidity program is about minting tokens and burning tokens. The purpose of this program is to help understand tokens and get a feel on how it works in Solidity.

## Description

This program is a Solidity-based smart contract designed for minting and burning tokens on the Ethereum blockchain. It includes functions to create new tokens (mint) and destroy existing tokens (burn), allowing for dynamic management of token supply. This contract serves as a foundational example for developers looking to understand the basic operations of token supply control in Solidity, providing a stepping stone for more advanced token management systems in the future.

## Getting Started

### Creating the program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., myToken.sol). Copy and paste the following code into the file:
```javascript
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {

    // public variables here
    string public tokenName  = "DREW";
    string public tokenAbbrv  = "DRO";
    uint public totalSupply = 0;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // burn function
    function burn(address _address, uint _value) public {
        if (balances[_address] >= _value) {
            totalSupply -= _value;
            balances[_address] -= _value;
        }
    }
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile myToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can scroll down to see the deployed contract in the "Deployed/Unpinned Contracts" section. 

### Executing the program

To mint tokens, click on the "MyToken" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "mint" function. Next, input the address of an account in the _address textfield and the amount of tokens to mint in the _value textfield. Finally, click on the "transact" button to execute the function and mint tokens on the account that was inputted.

To burn tokens, click on the "MyToken" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "burn" function. Next, input the address of an account in the _address textfield and the amount of tokens to burn in the _value textfield. Finally, click on the "transact" button to execute the function and burn tokens on the account that was inputted.

To check the balance or amount of tokens that an account has, click on the "MyToken" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "balances" function. Next, input the address of an account in the address textfield. Finally, click on the "call" button to execute the function and the amount of tokens of the account that was inputted will be displayed.

## Authors

Metacrafter napjoquino

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
