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
