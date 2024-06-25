#Project title
# MyToken Smart Contract 

#Description
This repository contains the Solidity code for the MyToken smart contract. This contract implements a basic token system with functionalities to mint and burn tokens. It is written in Solidity version 0.8.26 and is intended for deployment on the Ethereum blockchain.
## Getting Started

### Executing Program
1. Open Remix IDE or your preferred development environment.
2. Copy the MyToken contract code into a new Solidity file (e.g., MyToken.sol).
3. Compile the contract using Solidity version 0.8.26.
4. Deploy the contract to a local blockchain or any Ethereum testnet/mainnet.


#code
// SPDX-License-Identifier: MIT
pragma solidity 0.8.26;

contract MyToken {
    string public tokenName;
    string public tokenAbbrv;
    uint256 public totalSupply;
    mapping(address => uint256) public balances;

    constructor(string memory _name, string memory _abbrv) {
        tokenName = _name;
        tokenAbbrv = _abbrv;
    }

    function mint(address _to, uint256 _value) public payable {
        totalSupply += _value;
        balances[_to] += _value;
        payable(msg.sender).transfer(msg.value); // Transfer ether to contract owner
    }

    function burn(address _from, uint256 _value) public {
        require(balances[_from] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_from] -= _value;
        payable(_from).transfer(_value); // Transfer ether back to the address
    }
}
## Authors
Arpit
https://github.com/Arpit554
## License
This project is licensed under the MIT License - see the LICENSE file for details.
