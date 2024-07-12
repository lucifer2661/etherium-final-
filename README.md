Overview
This smart contract, written in Solidity, implements a simple ERC-20-like token named "Meta" with the abbreviation "MTA." The contract allows for minting new tokens and burning existing tokens, managing balances for each address that interacts with it.

Contract Details
Public Variables
string public tokenName: This is the name of the token, which is set to "Meta".
string public tokenAbbrv: This is the abbreviation of the token, which is set to "MTA".
uint public totalSupply: This keeps track of the total supply of tokens in circulation, initially set to 0.
Mappings
mapping(address => uint) public balances: This mapping stores the balance of each address. It maps an address to its respective token balance.
Functions
Mint Function
solidity
Copy code
function mint(address _address, uint _value) public {
    totalSupply += _value;
    balances[_address] += _value;
}
Purpose: The mint function creates new tokens and assigns them to a specified address.
Parameters:
_address: The address to which the new tokens will be assigned.
_value: The number of tokens to be created.
Functionality:
Increases the totalSupply by the _value.
Adds the _value to the balance of _address.
Burn Function
solidity
Copy code
function burn(address _address, uint _value) public {
    require(balances[_address] >= _value, "Insufficient balance to burn");
    totalSupply -= _value;
    balances[_address] -= _value;
}
Purpose: The burn function destroys existing tokens from a specified address.
Parameters:
_address: The address from which tokens will be burned.
_value: The number of tokens to be destroyed.
Functionality:
Checks if the _address has at least _value tokens. If not, it reverts with an error message "Insufficient balance to burn".
Decreases the totalSupply by the _value.
Subtracts the _value from the balance of _address.
Usage
Minting Tokens:

Call the mint function with the address and the amount of tokens to be created.
Example: mint(0x123..., 100) will create 100 tokens and assign them to the address 0x123....
Burning Tokens:

Call the burn function with the address and the amount of tokens to be destroyed.
Example: burn(0x123..., 50) will burn 50 tokens from the address 0x123... if it has at least 50 tokens.
Conclusion
This contract provides basic functionality for a token with minting and burning capabilities. It can be further extended to include more features such as transfer functions, allowances, and events for a fully compliant ERC-20 token.
