``` solidity
pragma solidity ^0.8.0;

contract Instance {

string public password;
uint8 public infoNum = 42;
string public theMethodName = 'The method name is method7123949.';
bool private cleared = false;

// constructor
constructor(string memory _password) {
    password = _password;
}

function info() public pure returns (string memory) {
    return 'You will find what you need in info1().';
}

function info1() public pure returns (string memory) {
    return 'Try info2(), but with "hello" as a parameter.';
}

function info2(string memory param) public pure returns (string memory) {
    if(keccak256(abi.encodePacked(param)) == keccak256(abi.encodePacked('hello'))) {
    return 'The property infoNum holds the number of the next info method to call.';
    }
    return 'Wrong parameter.';
}

function info42() public pure returns (string memory) {
    return 'theMethodName is the name of the next method.';
}

function method7123949() public pure returns (string memory) {
    return 'If you know the password, submit it to authenticate().';
}

function authenticate(string memory passkey) public {
    if(keccak256(abi.encodePacked(passkey)) == keccak256(abi.encodePacked(password))) {
    cleared = true;
    }
}

function getCleared() public view returns (bool) {
    return cleared;
}
}
```
```javascript
await contract.info()
'You will find what you need in info1().'

await contract.info1()
'Try info2(), but with "hello" as a parameter.'

await contract.info2('hello')
'The property infoNum holds the number of the next info method to call.'

await contract.infoNum()
i {negative: 0, words: Array(2), length: 1, red: null}
length: 1
negative: 0
red: null
words: (2) [42, empty]
[[Prototype]]: Object


await contract.info42()
'theMethodName is the name of the next method.'


await contract.theMethodName()
'The method name is method7123949.'


await contract.method7123949()
'If you know the password, submit it to authenticate().'



contract.abi
(11) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
0: {inputs: Array(1), stateMutability: 'nonpayable', type: 'constructor', constant: undefined, payable: undefined}
1: {inputs: Array(1), name: 'authenticate', outputs: Array(0), stateMutability: 'nonpayable', type: 'function', …}
2: {inputs: Array(0), name: 'getCleared', outputs: Array(1), stateMutability: 'view', type: 'function', …}
3: {inputs: Array(0), name: 'info', outputs: Array(1), stateMutability: 'pure', type: 'function', …}
4: {inputs: Array(0), name: 'info1', outputs: Array(1), stateMutability: 'pure', type: 'function', …}
5: {inputs: Array(1), name: 'info2', outputs: Array(1), stateMutability: 'pure', type: 'function', …}
6: {inputs: Array(0), name: 'info42', outputs: Array(1), stateMutability: 'pure', type: 'function', …}
7: {inputs: Array(0), name: 'infoNum', outputs: Array(1), stateMutability: 'view', type: 'function', …}
8: {inputs: Array(0), name: 'method7123949', outputs: Array(1), stateMutability: 'pure', type: 'function', …}
9: {inputs: Array(0), name: 'password', outputs: Array(1), stateMutability: 'view', type: 'function', …}
10: {inputs: Array(0), name: 'theMethodName', outputs: Array(1), stateMutability: 'view', type: 'function', …}



await contract.password()
'ethernaut0'


await contract.authenticate('ethernaut0');
 ⛏️ Sent transaction ⛏ 
 ⛏️ Mined transaction ⛏ 
 ⛏️ Submitting level instance... <  < <<PLEASE WAIT>> >  > ⛏️
 ⛏️ Sent transaction ⛏
 ⛏️ Mined transaction ⛏ 
 ( ͡° ͜ʖ ͡°) Well done, You have completed this level!!!
