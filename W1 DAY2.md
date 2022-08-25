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
        uint accNumber;
        string branch;
        uint balance;
    }
    uint[] no; 
    uint[] name;
    string[] brh;
    uint[] balc;

    uint[] acNumbercount;   // array storing account numbers 
    address[] addresses;     // array storing addresses 

    userdata[] public arrayuserdata;   
    bankdata[] public arraybankdata;

    mapping(address=>mapping(uint=>bankaccount)) public mappedbankaccount;

    function setInfo(uint _number,uint _bank,string memory _branch,uint _balance) public 
    {
        mappedbankaccount[msg.sender][_number]=bankaccount(_bank,_branch,_balance,true);
        acNumbercount.push(_number);
        addresses.push(msg.sender);
        no.push(_bank);
        name.push(_bank);
        brh.push(_branch);
        balc.push(_balance);
         
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
        
        userdata[] memory muserdata= new userdata[](acNumbercount.length);

        for(uint i=0;i<acNumbercount.length;i++)
        {
            if(mappedbankaccount[msg.sender][acNumbercount[i]].exists == true){
            userdata memory newuserdata=userdata(acNumbercount[i],no[i],brh[i],balc[i]);
            muserdata[i]=newuserdata;

          
            
            }
        }
        return muserdata;
        
    }

    function getDataOfBank(uint _name) public view returns(bankdata[] memory )
    {
        uint count;
        bankdata[] memory mbankdata= new bankdata[](acNumbercount.length); // new array to store struct 

        for(uint i=0;i<addresses.length;i++)
        {
            for(uint j=0;j<acNumbercount.length;j++)
            {
                if(mappedbankaccount[addresses[i]][acNumbercount[j]].bank_name ==_name)
                {
                    // new struct to store data 
                bankdata memory newbankdata=bankdata(acNumbercount[j],mappedbankaccount[addresses[i]][acNumbercount[j]].branch,mappedbankaccount[addresses[i]][acNumbercount[j]].balance);
                mbankdata[i]=newbankdata;
                count++;
                }
            }        
        }
        return mbankdata;
        
    }


    

}
