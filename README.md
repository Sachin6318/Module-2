# Create Function Frontend
This Solidity program is a simple smart contract to create your own"Function Frontend" and deploy it using Remix". It demonstrates the basic syntax and functionality of the Function Frontend in the Solidity programming language. The purpose of this program is to serve as a starting point for those who are new to "Function Frontend" in Solidity and want to get a feel for how it works.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. It is a simple smart contract to create your own "Function Frontend" and deploy it using Remix. This program serves as a simple and straightforward introduction to "Function Frontend" in Solidity programming, and can be used as a stepping stone for more complex projects in the future.

## Getting Started

Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:



       
     // SPDX-License-Identifier: UNLICENSED
     pragma solidity ^0.8.9;

    contract Assessment {
    address payable public owner;
    uint256 public balance;

    event Deposit(uint256 amount);
    event Withdraw(uint256 amount);
    event Transfer(address indexed to, uint256 amount);

    constructor(uint initBalance) payable {
        owner = payable(msg.sender);
        balance = initBalance;
    }

    function getBalance() public view returns(uint256) {
        return balance;
    }

    function deposit(uint256 _amount) public payable {
        uint _previousBalance = balance;
        require(msg.sender == owner, "You are not the owner of this account");
        balance += _amount;
        assert(balance == _previousBalance + _amount);
        emit Deposit(_amount);
    }

    error InsufficientBalance(uint256 balance, uint256 withdrawAmount);

    function withdraw(uint256 _withdrawAmount) public {
        require(msg.sender == owner, "You are not the owner of this account");
        uint _previousBalance = balance;
        if (balance < _withdrawAmount) {
            revert InsufficientBalance({balance: balance, withdrawAmount: _withdrawAmount});
        }
        balance -= _withdrawAmount;
        assert(balance == (_previousBalance - _withdrawAmount));
        emit Withdraw(_withdrawAmount);
    }

    function transfer(address payable _to, uint256 _amount) public {
        require(msg.sender == owner, "You are not the owner of this account");
        uint _previousBalance = balance;
        if (balance < _amount) {
            revert InsufficientBalance({balance: balance, withdrawAmount: _amount});
        }
        balance -= _amount;
        _to.transfer(_amount);
        assert(balance == (_previousBalance - _amount));
        emit Transfer(_to, _amount);
    }

    function changeOwner(address payable _newOwner) public {
        require(msg.sender == owner, "You are not the owner of this account");
        owner = _newOwner;
    }
     }


To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.20" (or another compatible version), and then click on the "Compile" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar.
## Authors

Sachin Singh

@Sachin17234

sachinsingh6318@gmail.com


## License

This project is licensed under the MIT License.
