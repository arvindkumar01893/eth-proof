# MyToken

MyToken is a simple ERC-20 like token smart contract implemented in Solidity. It allows for basic token operations such as minting and burning.

## Contract Details

- **Name:** MyToken
- **Compiler Version:** 0.8.0

## Variables

- `name` (string): The name of the token.
- `symbol` (string): The symbol of the token.
- `totalSupply` (uint): The total supply of the token.
- `balances` (mapping): A mapping to store the balance of each address.

## Functions

### Constructor

```solidity
constructor(string memory _name, string memory _symbol, uint _initialSupply)
```
The constructor initializes the token with a name, symbol, and an initial supply. The initial supply is assigned to the contract deployer's address.

## Mint Function

```solidity
function mint(address to, uint amount) public
```
This function mints new tokens and assigns them to the specified address. It increases the total supply of the token by the specified amount.

```solidity
function burn(address from, uint amount) public
```
This function burns tokens from the specified address. It decreases the total supply of the token by the specified amount. The function requires that the address has a sufficient balance to burn.

## Usage
### Deploying the Contract
Deploy the MyToken contract with the desired name, symbol, and initial supply.

### Minting Tokens
Call the mint function with the recipient's address and the amount of tokens to be minted.

```solidity
mint(address to, uint amount)
```

### Burning Tokens
Call the burn function with the address from which tokens are to be burned and the amount of tokens to be burned.

```solidity
burn(address from, uint amount)
```
### example
```solidity
pragma solidity ^0.8.0;

contract MyToken {

    // public variables here
    string public name;
    string public symbol;
    uint public totalSupply;

    // mapping variable here
    mapping(address => uint) public balances;

    constructor(string memory _name, string memory _symbol, uint _initialSupply) {
        name = _name;
        symbol = _symbol;
        totalSupply = _initialSupply;
        balances[msg.sender] = _initialSupply;
    }

    // mint function
    function mint(address to, uint amount) public {
        totalSupply += amount;
        balances[to] += amount;
    }

    // burn function
    function burn(address from, uint amount) public {
        require(balances[from] >= amount, "Insufficient balance to burn");
        totalSupply -= amount;
        balances[from] -= amount;
    }

}
```
### license
This project is licensed under the MIT License.
