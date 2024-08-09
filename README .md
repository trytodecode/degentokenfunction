# Degen Token
it provides us functionality to peform minting burning and trasfering of token . 

## Description

this is the project created to demonstrate the use ofdegen token created on fuji netwokr using avalanche to interact with contract and with their function like minting , burning and transfering .

## Getting Started

### Installing

* to deploy this code you need to have remix or any IDE.
* need compiler for solidity 
* login to snowtrace 
* required version of solidity compiler is (version ^0.8.20)

### Executing program

*to deploy this block of code you need an IDE of  solidity
* after that copy paste the given block of code in your IDE
* then set compiler to version (0.8.20)
* in code section we have imported the openzepline and hadhart .
* then in deploy section paste the address of your metamask  account.
* after that you will observe that contract is deployed and we re ready to interact 
* now you can perform opertion of the contract  and verify using snowtrace .


// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract Degen is ERC20, ERC20Burnable, Ownable {
    constructor() ERC20("degen", "DGN") Ownable(msg.sender) {}



    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    function balance() external view returns (uint256)
    {
        return this.balanceOf(msg.sender);
    }

    function tranfer(address to,uint value) external returns (string memory)
    {
        require(balanceOf(msg.sender)>=value);
        approve(msg.sender, value);
        transferFrom(msg.sender, to, value);
        return "success";
    }
    function storeinfo() external pure returns ( string memory){
        return "1. GAME NFT  100tokens 2. GAME TSHIRT  750 tokens   3. ACCESSORIES 500 tokens";
    }

    function redeemTokens(uint256 _value) external {
        require(_value > 0, "Invalid token value");
        require(balanceOf(msg.sender) >= _value, "Insufficient balance");
        if (_value==1)
            {_burn(msg.sender, 100);}
        else if(_value==2)
        {
            _burn(msg.sender, 750);
        }
        else if(_value==3)
        {
            _burn(msg.sender, 500);
        }
    }
}

## Help
* make sure your IDE is for solidity 

* make sure you safe search in brave browser is off 

* need to write address in deploy section or you will stuck there .

* make sure your compiler is set to version (0.8.20) otherwise error will throw

## Authors
kumar sanjeev 
https://www.linkedin.com/in/kumar-sanjeev-150965230/


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
