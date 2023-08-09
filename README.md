#RamosToken
This project involves writing a smart contract that establishes a new cryptocurrency token on the Ethereum blockchain. The contract includes functionalities for minting new tokens, burning (destroying) existing tokens, and ensuring proper checks are in place to maintain the integrity of the token system.
##Description
This project involves creating a contract for a cryptocurrency token. The contract will include public variables to store information about the token (Token Name, Token Abbreviation, Total Supply), a mapping of addresses to token balances, a mint function to increase the total supply and balance of an address, a burn function to decrease the total supply and balance, and specific conditions in the burn function to ensure that the account balance is sufficient for the amount being burned.
###Executing program
contract RamosToken
    {
        // public variables here
            string public tokenName;
            string public tokenAbbrv;
            uint public TotalSupply;
        // mapping variable here
            mapping(address => uint) balances;

            constructor(string memory name, string memory Abbrv, uint initialSupply){
                tokenName = name;
                tokenAbbrv = Abbrv;
                TotalSupply = initialSupply;
                balances[msg.sender] = initialSupply;
            }
        // mint function
            function mint(address account, uint value) public {
                TotalSupply = value;
                balances[account] += value;
            }
        // burn function 
            function burn(address account, uint value) public {
                require(balances[account] >= value, "Insufficient balance");
                TotalSupply -= value;
                balances[account] -= value;
            }

            function getBalance(address account) public view returns (uint){
                return balances[account];
            }   
    }   
##License
This project is licensed under the MIT License - see the LICENSE.md file for details
