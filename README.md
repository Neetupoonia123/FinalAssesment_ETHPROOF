# FinalAssesment_ETHPROOF
In this program we have created a token and implemented its basic charactersticts. The following characteristics of the basic token implemented by this Solidity contract:

# Public Variables:
TokenName: Holds the name of the token in human readable form (by default, "TheMetaCrafter").
TokenAbbrv: This is an abbreviation for the token ("TMC" by default).
TotalSupply: Initially initialized to 0, this variable tracks the total number of tokens in circulation.

Block of code that immplements these public variable:

string public TokenName ="TheMetaCrafter";
string public TokenAbbry ="TMC";
uint public TotalSupply = 0;

# Balance Mapping:
A public mapping called "balance" keeps track of each address's token balance.

Block of code that implements Mapping:

mapping(address => uint) public balance;

# Minting Functionality:
The functionality of minting is as follows: 
mint(address _address, uint _value): Lets authorized parties mint new tokens and add them to the total supply and the recipient's address (_address).

Block of code implementing Minting functionality:

function mint(address _address, uint _value) public{
  TotalSupply += _value; //TotalSupply = TotalSupply + _value
  balance[_address] += _value;
}

# Burning Functionality:
The functionality of Burning is as follows:
burn(address _address, uint _value): Allows tokens to be burned, thereby eliminating them from the supply overall and the balance of the given address (_address). 
Before burning, a safety check (requirement statement) is included to make sure there is enough balance.

Block of code implementing Burning function:

function burn(address _address, uint _value) public{
  require(balance[_address] >= _value, "Insufficient balance for burning");  //Use of require statement to confirm that there are enough tokens before burning.
  TotalSupply -= _value;
  balance[_address] -= _value;
}
