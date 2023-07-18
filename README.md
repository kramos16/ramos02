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
