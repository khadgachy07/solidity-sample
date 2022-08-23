
## viewpure 
```bash
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.9;

contract viewpure {

uint public num;

// pure : no read, no write of num
function getter1(uint num1, uint num2) public pure returns(uint)
{
    uint c;
    c=num1+num2;
    return c;
}

// modify of num , so normal 
function getter2(uint num1, uint num2) public returns(uint)
{
   
   num=num1+num2;
    return num;
}


// only read of num value 
function getter3(uint num1,uint num2) public view returns(uint)
{

uint b;
b=num+num1+num2;
return b;

}
} 
```

## modifier 
can take an inputs too.....
```bash
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;
contract modidiertest {
    address public owner;

uint public num;
constructor () {
 owner=msg.sender;
}

modifier onlyOwner{

    require(owner==msg.sender,"only owner can call this function");
    _;
}

modifier validAddress(address _addrr) {

    require(_addrr!=address(0),"invalid address");
    _;

}

function adder(uint a,uint b) public view onlyOwner returns(uint )
{
   return a+b;
}

function changeOwner(address _addrr) public onlyOwner validAddress(_addrr) 
{
    owner=_addrr; 
}

}

```


## operators 
-ternary opeartors
```bash

//SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;


contract operators {

	uint public a = 20;
    uint public b = 30;

    bool public grt=a>b;
    bool public less=a<b;

    string name = 'hari';

    function test1(uint num1) public view returns (string memory desc ) 
    // testing operators so code opt is ignored here for now 
    {
        if (num1==a) {
            desc="number is equal ";
        }
        if (num1>a)
        {
            desc="number is greater than a";
            
        }
        else if (num1<a)
        {

            desc="number is less than a  ";
            
        }
    }

function findsub (uint num1,uint num2) public pure returns (uint)
{
    uint sub= num1>num2 ? num1-num2: num2-num1; 
    return sub;
}
function checkgrt (uint num1,uint num2) public pure returns (string memory)
{
    string memory desc= num1>num2 ?"num1 is greater": "num2 is greater"; 
    return desc;
}
function 
}
 
```


## enum 
```bash
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13; 


contract enumprac{


    enum status{
        hired,
        rejected
    }
  address public owner;
  constructor()
  {
      owner=msg.sender;
  }
 status public currentstatus=status.rejected;

 modifier onlyManager(){
     require(owner==msg.sender,"you are not a owner");
     _;
 }

 function changeToHired() public onlyManager
 {

    currentstatus=status.hired;
 }


}
-------------------------------------Tbc--------------------------------------------------------------
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13; 


contract enumprac{

     enum status {
         notOrdered,
         ordered,
         pending,
         shipped,
         delivered
     }

     address public owner;

     constructor(){
         owner=msg.sender;
     }


    modifier onlyManager()
    {
        require(owner==msg.sender,"you are not a owner");
        _;
    }

    status public currentStatus=status.notOrdered;



    function buy() public 
    {
        currentStatus=status.ordered;
    }

    function changeStatus( ) public {

        
        
    }



}
```


## array 
```bash

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13; 


contract array{

uint[] public arr;
uint public getSizeofArray;

    function push_array(uint num) public returns(uint[] memory)
    {
     arr.push(num);
     getSizeofArray++;
     return arr;
    }

    function pop_array() public {
    
    arr.pop();
    getSizeofArray--;

    }
}

```


##    
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


## 
```bash
```


