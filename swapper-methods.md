# Novation Sell-less Swapper

## Contract

[0x2085B84912531B126f1C92cd70A71381713f0795](https://bscscan.com/address/0x2085B84912531B126f1C92cd70A71381713f0795)

## Interface

```typescript
interface Swapper {
    // In case of buy the "_token", it calculates output amount from input amount including amount after tax
    function getAmountOutFromBuy(
        address _token, 
        uint _amountIn
    ) public view returns (uint amountOut, uint afterTax);
    
    // In case of buy the "_token", it calculates input amount from output amount including amount after tax
    function getAmountInFromBuy(
        address _token, 
        uint _amountOut
    ) public view returns (uint amountIn, uint afterTax);
    
    // In case of sell the "_token", it calculates output amount from input amount including amount after tax
    function getAmountOutFromSell(
        address _token, 
        uint _amountIn
    ) public view returns (uint amountOut, uint afterTax);

    // In case of sell the "_token", it calculates input amount from output amount including amount after tax
    function getAmountInFromSell(
        address _token, 
        uint _amountOut
    ) public view returns (uint amountIn, uint afterTax);

    // It returns buy tax and sell tax for the "_token"
    function getTotalFee(
        address _token
    ) public view returns (uint buyFee, uint sellFee);

    // It buys the "_token" from the BNB with giving the minimum out amount
    function buy(
        address _token, 
        uint _amountOutMin
    ) external payable;

    // It sells the "_token" to the BNB with giving the minimum out amount
    function sell(
        address _token, 
        uint _amountIn, 
        uint _amountOutMin
    ) external;
}
```