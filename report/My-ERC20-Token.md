```solidity

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract my ERC20Token {

import "./IERC20.sol";

contract new_Token{
    string name;
    string symbol;
    uint256 decimal;
    uint256 totalSupply;
    uint256 minimint = 10e18;
    uint256 maximint = 1_000_000e18;
  
    mapping(address => uint256) public balances;
mapping(address => mapping(address => uint256))public allowances;

    constructor (string memory _name, string memory _symbol,
     uint256 _decimal,
    uint256 _totalSupply) { 
        name = _name;
        symbol = _symbol;
        decimal = _decimal;
        totalSupply = _totalSupply;}

        function balanceOf( address _user) external view returns ( uint256
        balance) { return balances[_user];}
        function tranferFrom( address _from, address _to, uint256 _amount) external returns ( bool success) {}

        function approve( address _spender, uint256 _value) external returns ( bool success) {
             require(balances[msg.sender] >= _value && _spender != address (0));
             allowances[msg.sender][_spender] = _value;
             return true;
        }
       
       function allowance(address _owner, address _spender) external view returns(
        uint256 remaining) { return allowances[_owner][_spender]; }
       
        function mint( address to, uint256 amount) external returns
        (uint256 
        ) { require(to != address (0)," can't mint to address (0)");
        if ( amount > minimint && amount <= maximint){
            balances[msg.sender] += amount;}
            return amount;
        }
        function burn(address _from, uint256 _amount) external
        { require(balances[msg.sender] >= _amount && _amount >0,
        "can't burn from address (0)");
        balances[_from] -= _amount;}
        
        function transfer( address _from, 
        address _to, uint256 _amount) external returns
     (bool success){ require(balances[msg.sender] >= _amount && _amount
     > 0, " can't transfer from address 0"); if (_from != address (0) 
     && _to != address(0))
     { balances[_from] -= _amount;
     balances[_to] += _amount;}
     return true;}  

     function transferFrom (address _from, address _to, uint256 _amount) external returns  (bool success) {
        require(allowances[_from][_to] >=_amount && _amount >0, "invalid transfer");
        allowances[_from][_to] -= _amount;
        balances[_from] -= _amount;
        balances[_to] -= _amount;
        return true;
        
     }}   }
```
