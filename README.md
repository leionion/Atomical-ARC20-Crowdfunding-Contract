# Atomical-ARC20-Crowdfunding-Contract
The Atomical-ARC20-Crowdfunding-Contract is a crowdfunding contract released by the Atomicals Protocol, utilizing ARC-20 tokens for fundraising, with deployers able to set parameters such as a block height time limit and an authorized public key for token withdrawal post-time limit via the Atomicals Virtual Machine (AVM).


####  1. Methods 

##### 1.1 name
```
function name() public view returns (string)
```
- Returns the name of the token - e.g. "MyToken".
- **OPTIONAL** - This method can be used to improve usability, but interfaces and other contracts MUST NOT expect these values to be present.

##### 1.2 symbol
```
function symbol() public view returns (string)
```
- Returns the symbol of the token. E.g. “ARC”.
- This method can be used to improve usability
- **NOTE** - This method is optional in EIP20. In ARC20, this is a required method. Tokens which don’t implement this method will never flow across the Areon.

##### 1.3 decimals
```
function decimals() public view returns (uint8)
```
- Returns the number of decimals the token uses - e.g. 8, means to divide the token amount by 100000000 to get its user representation.
- This method can be used to improve usability
- **NOTE** - This method is optional in EIP20. In ARC20, this is a required method. Tokens which don’t implement this method will never flow across the Areon.

##### 1.4 totalSupply
```
function totalSupply() public view returns (uint256)
```
- Returns the total token supply. 

##### 1.5 balanceOf
```
function balanceOf(address _owner) public view returns (uint256 balance)
```
- Returns the account balance of another account with address `_owner`.

##### 1.6 getOwner
```
function getOwner() external view returns (address);
```
- Returns the ARC20 token owner which is necessary for binding with ARC20 token.
- **NOTE** - This is an extended method of EIP20. Tokens which don’t implement this method will never flow across the Areon.

##### 1.7 transfer
```
function transfer(address _to, uint256 _value) public returns (bool success)
```
- Transfers `_value` amount of tokens to address `_to`, and MUST fire the Transfer event. The function SHOULD throw if the message caller’s account balance does not have enough tokens to spend.
- **NOTE** - Transfers of 0 values MUST be treated as normal transfers and fire the Transfer event.

##### 1.8 transferFrom
```
function transferFrom(address _from, address _to, uint256 _value) public returns (bool success)
```
- Transfers `_value` amount of tokens from address `_from` to address `_to`, and MUST fire the Transfer event.
- The transferFrom method is used for a withdraw workflow, allowing contracts to transfer tokens on your behalf. This can be used for example to allow a contract to transfer tokens on your behalf and/or to charge fees in sub-currencies. The function SHOULD throw unless the `_from` account has deliberately authorized the sender of the message via some mechanism.
- **NOTE** - Transfers of 0 values MUST be treated as normal transfers and fire the Transfer event.

##### 1.9 approve
```
function approve(address _spender, uint256 _value) public returns (bool success)
```
- Allows `_spender` to withdraw from your account multiple times, up to the `_value` amount. If this function is called again it overwrites the current allowance with `_value`.
- **NOTE** - To prevent attack vectors like the one described here and discussed here, clients SHOULD make sure to create user interfaces in such a way that they set the allowance first to 0 before setting it to another value for the same spender. THOUGH The contract itself shouldn’t enforce it, to allow backwards compatibility with contracts deployed before

##### 1.10 allowance
```
function allowance(address _owner, address _spender) public view returns (uint256 remaining)
```
- Returns the amount which `_spender` is still allowed to withdraw from `_owner`.

#### 2. Events

##### 2.1 Transfer
```
event Transfer(address indexed _from, address indexed _to, uint256 _value)
```
- **MUST** trigger when tokens are transferred, including zero value transfers.
- A token contract which creates new tokens SHOULD trigger a Transfer event with the `_from` address set to 0x0 when tokens are created.

##### 2.2 Approval
```
event Approval(address indexed _owner, address indexed _spender, uint256 _value)
```
**MUST** trigger on any successful call to `approve(address _spender, uint256 _value)`.


### 3. A sample ARC20 Contract
[ARC20_Crowdfunding_Contract.sol](ARC20_Crowdfunding_Contract.sol)

### Contact Info:
If you have technical issues & development inquiries, please contact me.

Twitter: https://x.com/chain_sats/
Telegram: https://t.me/inscNix/
