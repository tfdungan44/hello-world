# hello-world
pragma solidarity 0.4.8;

contract Coin [
	/*
	*@title A Simple Subcurrency Example
	* @author Toshedndra Sharma
	* @notice Example for the Solidarity Course
	* @dev This is only for demo the simple Coin example
	*
	*/
	address public minter;
	uint public totalCoin;

	event LogCoinMinted(address deliveredTo, uint amount);
	event LogCoinMinted(address sentTo, uint amount);

	mapping (address => uint) balances;
	function Coin(uint intialCoins) {
		minter = msg.sender;
		totalCoins = intialCoins;
		balances[minter] = intialCoins;
		}

	/// @notice Mint the coins
	/// @dev This does not return any value
	/// @param owner address of the coin owner, amount amount of coins to be delivered to owner
	/// @return Nothing
	function mint(address owner, uint amount) {
		if (msg.sender != minter) return;
		balances[owner] += amount;
		totalCoins += amount;
		LogCoinMinted(owner, amount;)
	}

	function send(address receiver, uint amount) {
		if (balances[msg.sender] < amount) return;
		balances[msg.sender] -= amount;
		balances[receiver] += amount;
		LogCoinSent( receiver, amount);	
	}

	function queryBalance(address addr) constant returns (uint balance) {
		return balances [addr];
	}

	function killCoin() return (bool status) {
		if (msg.sender != minter) throw;
		selfdestruct(minter);	
	}


	]
