# SmartContractProject

This Solidity program is about event registration. The purpose of this program is to help understand the statements require(), revert(), and assert().

## Description

This program is a Solidity-based smart contract designed to help developers understand and utilize the require(), revert(), and assert() statements for error handling in Solidity. It includes functions to register and update the user's information, showcasing how these statements can be used to enforce conditions, revert transactions, and ensure correctness in smart contract operations. This contract serves as a foundational example for developers looking to grasp the basic error handling mechanisms in Solidity, providing a stepping stone for more advanced smart contract development.

## Getting Started

### Creating the program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., myProject1.sol). Copy and paste the following code into the file:
```javascript
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract EventRegistration {
    address public owner;
    uint public maxParticipants;
    uint public registeredCount;
    bool public registrationOpen;

    struct Participant {
        string name;
        uint age;
        bool registered;
    }

    mapping(address => Participant) public participants;

    constructor(uint _maxParticipants) {
        owner = msg.sender;
        maxParticipants = _maxParticipants;
        registeredCount = 0;
        registrationOpen = true;
    }

    // Modifier to check if the caller is the owner
    modifier onlyOwner() {
        require(msg.sender == owner, "Only owner can perform this action");
        _;
    }

    // Function to register a participant
    function register(string memory _name, uint _age) public {
        // Require statements to validate inputs and conditions
        require(registrationOpen, "Registration is closed");
        require(_age > 0, "Age must be greater than 0");
        require(!participants[msg.sender].registered, "You are already registered");
        require(registeredCount < maxParticipants, "Event is full");

        // Register the participant
        participants[msg.sender] = Participant(_name, _age, true);
        registeredCount += 1;
    }

    // Function to close the registration by the owner
    function closeRegistration() public onlyOwner {
        require(registrationOpen, "Registration is already closed");
        registrationOpen = false;
    }

    // Function to assert that the contract is in a valid state
    function checkInvariant() public view {
        assert(registeredCount <= maxParticipants);
    }

    // Function to update participant's information, using revert for complex conditions
    function updateParticipant(string memory _name, uint _age) public {
        if (_age <= 0) {
            revert("Age must be greater than 0");
        }
        if (!participants[msg.sender].registered) {
            revert("You are not registered");
        }
        
        participants[msg.sender].name = _name;
        participants[msg.sender].age = _age;
    }

}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile myProject1.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "EventRegistration" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can scroll down to see the deployed contract in the "Deployed/Unpinned Contracts" section. 

### Executing the program

To register, click on the "EventRegistration" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "register" function. Next, input the name in the _name textfield and the age in the _age textfield. Finally, click on the "transact" button to execute the function and register the details that was inputted.

To update your user information, click on the "EventRegistration" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "updateParticipant" function. Next, input the name in the _name textfield and the age in the _age textfield. Finally, click on the "transact" button to execute the function and update the details that was inputted.

To close the registration, click on the "EventRegistration" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "closeRegistration" function. The function will only be executed successfully if the owner was the one who called the function. Once the "closeRegistration" function has been clicked by the owner, the registration will be closed.

To check any invariants, click on the "EventRegistration" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "checkInvariant" function. Once the "checkInvariant"  function has been clicked, it will check if the contract had any internal issues with the computations.

To check the max limit of participants for the event, click on the "EventRegistration" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "maxParticipants" function. Once the "maxParticipants" function has been clicked, it will display a number which shows the max limit of participants.

To check the address of the owner, click on the "EventRegistration" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "owner" function. Once the "owner" function has been clicked, it will display the address of the owner.

To check details for a participant, click on the "EventRegistration" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "participants" function. Next, input the address of the participant in the textfield. Finally, click on the "call" button to execute the function and it will display the details of that specific participant.

To check the max limit of participants for the event, click on the "EventRegistration" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "registeredCount" function. Once the "registeredCount" function has been clicked, it will display a number which shows the number of participants registered.

To check if the registration of the event is still open, click on the "EventRegistration" contract in the left-hand sidebar in the "Deployed/Unpinned Contracts" section, and then click on the "registrationOpen" function. Once the "registrationOpen" function has been clicked, it will display a boolean which shows true or false.

## Authors

Metacrafter napjoquino

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
