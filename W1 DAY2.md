// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;  

contract bankinfo{


    struct bankaccount {
        uint bank_name;
        string branch;
        uint balance;
        bool exists;
    }

    struct userdata{
        uint accNumber;
        uint bank_name;
        string branch;
        uint balance;

    }

    struct bankdata {
        string accNumber;
        string branch;
        uint balance;
    }


    uint[] acNumbercount;    // array storing account numbers 
    address[] addresses;     // array storing addresses 

    userdata[] public arrayuserdata;   
    bankdata[] public arraybankdata;

    mapping(address=>mapping(uint=>bankaccount)) public mappedbankaccount;

    function setInfo(uint _number,uint _bank, string memory _branch,uint _balance) public 
    {
        mappedbankaccount[msg.sender][_number]=bankaccount(_bank,_branch,_balance,true);
        acNumbercount.push(_number);
        addresses.push(msg.sender);
         
    }


    function deposit(uint _number,uint _balance) public 
    {
        mappedbankaccount[msg.sender][_number].balance+=_balance;   
    }


     function withdraw(uint _number,uint _balance) public 
    {
        mappedbankaccount[msg.sender][_number].balance-=_balance;   
    }

    function getDataOfUser() public view returns(userdata[] memory )
    {
        uint count;
        userdata[] memory muserdata= new userdata[](acNumbercount.length);

        for(uint i=0;i<acNumbercount.length;i++)
        {
            if(mappedbankaccount[msg.sender][acNumbercount[i]].exists == true){
            userdata memory newuserdata=userdata(acNumbercount[i],mappedbankaccount[msg.sender][i].bank_name,mappedbankaccount[msg.sender][i].branch,mappedbankaccount[msg.sender][i].balance);
            muserdata[i]=newuserdata;
            count++;
            }
        }
        return muserdata;
        
    }


    

}
