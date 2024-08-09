// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.4.16 <0.9.0;

contract rawcoin_ico{

    //Introducting the maximum number of rawcoins available for sale
    uint public max_rawcoins = 1000000;

    //Intoducing the USD to rawcoins conversion rate
    uint public usd_to_rawcoins = 1000;

    //Introductcing the total number of rawcoins that have been bought by the investors
    uint public total_rawcoins_bought =0;

    //Mapping from the investor address to its equity in rawcoins and USD
    mapping(address => uint) equity_rawcoins;
    mapping(address => uint) equity_usd; 

    //checking is an investor can buy rawcoins
    modifier can_buy_rawcoins(uint usd_invested){
        require(usd_invested * usd_to_rawcoins + total_rawcoins_bought <= max_rawcoins );
        _;//underscore(_)is to say that The function to which we will link the modifier will only be applied if the condition is verified, that is if the condition is true
    }

    //Getting the equity in rawcoins of an investor
    function equity_in_rawcoins(address investor) external view returns(uint){
        return equity_rawcoins[investor];
    }

    //Getting the equity in USD of an investor
    function equity_in_usd(address investor) external view returns(uint){
        return equity_usd[investor];
    }

    //Buying rawcoins
    function buy_rawcoins(address investor, uint usd_invested) external can_buy_rawcoins(usd_invested){
        uint rawcoins_bought = usd_invested * usd_to_rawcoins;
        equity_rawcoins[investor] += rawcoins_bought;//equity the investor hold person/investor1 -> 5000 rawcoins. 5*1000 = 5000 rawcoins
        equity_usd[investor] = equity_rawcoins[investor]/1000;// 5000/1000 = 5 daollars invester {inestor1 -> 5 USD}
        total_rawcoins_bought += rawcoins_bought;

    }
    //Selling rawcoins
    function sell_rawcoins(address investor, uint rawcoins_sold) external{
        equity_rawcoins[investor] -= rawcoins_sold;// 5 - 1 = 4 
        equity_usd[investor] = equity_rawcoins[investor]/1000;
        total_rawcoins_bought -= rawcoins_sold;
    }
}

