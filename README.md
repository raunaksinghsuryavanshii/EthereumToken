# EthereumToken
Welcome to the "Ethproof Beginner Course Project" GitHub project from Metacrafters! This repository acts as the focal point for all the code and project-related materials connected to the Metacrafters' Ethproof Beginner Course.

INTRODUCTION

A hands-on education project called "Ethproof Beginner Course Project" by Metacrafters focuses on the fundamentals of Ethereum programming. Creating a simple token minting and burning smart contract in Solidity is the main task of this project. Through this interesting project, participants will learn how to write secure smart contracts, interact with the Ethereum blockchain, and comprehend the fundamental ideas of tokenomics.

SMART CONTRACT LICENSE

License: This contract is released under the MIT License, as indicated in the license comment at the top of the code.
Solidity Version: The contract is written in Solidity version 0.8.18, ensuring compatibility with the specified version.

CODE EXPLANATION

The token's name and symbol are defined by the variables tokenName and tokenSymbol. The total supply of tokens is tracked by totalSupply. A mapping called balances maintains track of the token balances for each address. Using the mint function, new tokens can be created and assigned to a given address. It raises the overall supply and needs a legitimate recipient address. Using the burn function, an address is able to burn (destroy) its tokens. It reduces the supply and necessitates that the sender has enough tokens to burn.

The agreement specifies the following public variables:a string variable called tokenName that carries the token's name. tokenSymbol: A string variable that depicts the token's symbol or acronym. totalSupply:a variable with unsigned integer values that stores the quantity of tokens available overall.

Calculating Balances:

To maintain track of the token balances connected to Ethereum addresses, the contract employs a mapping called balances. Addresses of token holders are mapped to the quantity of tokens they possess.

Minting Tokens (function of the mint):

New tokens can be made using the mint function. Both _to (an Ethereum address) and _value (the quantity of tokens to mint) are required.

Interior of the function:

The minted value is added to totalSupply, thereby raising the total supply of tokens. The minted value adds to the balance of the _to address.Tokens being burned (burn function)

The burning of tokens is possible with the burn function. The _value parameter, which is the quantity of tokens to burn, is required.

Interior of the function:

Using a need statement, it determines whether the sender's (msg.sender's) balance is higher than or equal to _value. To make sure the sender has enough tokens to burn, this is a safety measure. If the sender has enough tokens, the burned value is subtracted from totalSupply, which effectively lowers the total supply of tokens. The burned value reduces the balance of the sender's address.

Congratulations! The Ethereum smart contract "Tokening" has been successfully deployed and tested. A fundamental framework for producing and administering tokens on the Ethereum blockchain is provided by this contract. 
As required, you can further modify and incorporate it into your projects.

CODE
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract EthToken {

    string public tokenName="Rajput";
    string public tokenSymbol="RSR";
    uint256 public totalSupply=100000;

    mapping(address => uint256) public balances;

    function mint(deal with _to, uint256 _value) public {
        totalSupply += _value;
        balances[_to] += _value;
    }

    function burn(uint256 _value) public  {
        require(balances[msg.sender] >= _value, "Low stability");
        totalSupply -= _value;
        balances[msg.sender] -= _value;
    }

}
