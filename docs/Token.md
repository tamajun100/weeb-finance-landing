# What is WEEB token?

WEEB token is the worlds first non-custodial yield farming token!

Unlike traditional staking and yield farming where you're required to give the custody (ownership) of your tokens to a secondary or a third party contract, with WEEB yield farming is an intrinsic feature.
Holding your tokens in an externally owned account (EOA, an account controlled by a private key) is enough to generate passive income.

With WEEB you're always farming and earning ($, ∞) (💲💰💵, ♾️🔁).

&nbsp;

Decentralized Finance (DeFi) presents a unique opportunity to people by providing access to variety of financial products thus financial freedom to more people.

Due to the diversity of the products and vastness of the space the investor has to constanly study the new products, learn their details, understand the risks, the constraints etc. which are sometimes not very well documented or not documented at all or simply confusing.
That increases the learning curve of making an investment and puts the investor in limbo state where either they don't invest or invest blindly.

&nbsp;

## Not in your wallet, not your money

In traditional staking and yield farming for the investor to generate passive income they have to transfer their tokens to a seperate staking or yield farming contract. This means *giving up the ownership* of the actual tokens in exchange of a potential return.

Although, the investor can see their staked amount and the potential reward ***there is difference between accessing and owning your tokens***.
Since the tokens are in the custody of the staking contract potential unwanted situations like unabling to withdraw before the lock up time, being charged for an earlier withdrawal, long unstaking periods of several days or longer, can arise when the investor tries to withdraw their tokens.
As a matter of fact, this can be done quite simply since the staking contract owns the tokens the investor is bound by the rules of the code. Isn't it a little disturbing?

&nbsp;

This is not the financial freedom we're dreaming about.
Knowing that, we designed WEEB to generate passive income without the requirement to transfer your tokens out from your wallet. You start to earn right away. You own your tokens and it is up to you to do whatever your want with them and whenever your want it.

Yield farming is a built-in feature of the WEEB token. Simple and easy, **buy and earn right away**!
No complicated steps, no confusing child tokens with strange names, no more forgetting where you staked your tokens, they're always in your wallet at your disposal!

### **This is the easiest form of passive income possible.**

&nbsp;

## Properties of the WEEB token

Along with the non-custodial yield farming model there are more unique properties that require explanation.

&nbsp;

### Dynamic, Temporary, Passive Supply (DTPS)

Unlike pre-minting huge amounts of tokens and creating diluted price from the beginning, WEEB uses dynamic supply model where tokens are minted as new blocks are mined.
This creates supply shortage and helps the price appreciation.

This model is also the backbone of the new hybrid yield farming model where investor receives minted WEEB tokens for their deposited assets where those received WEEB tokens act as locked balance inside their total balance which generate yield but are not tradable/transferrable. On return of the locked supply (could be partial returned) corresponding deposit is released and the returned tokens are burned thus supply is decreased.
[Ref. to Farms]

&nbsp;

### Holder Based Emission Suppression

To prevent early liquidity concentration and create more fair token distribution the emission is supressed and increased linearly with the number of token holders until certain amount of token holders are reached.
This is helpful especially in the early stages of the project where earlier investors get the bulk of the rewards which in turn allows of concentration of the liquidity in those few accounts creating potential sell pressure as the price increases.

[Insert holder vs emission graph here]

&nbsp;

### Inflation Regulation

Inflation is the source of the passive income generated by yield farming.
Tokens are minted for each block and distributed to the investors according to their balance shares amongst the all holders.

If the inflation is not absorbed by new investors or thru token burns it may start to have a negative effect on the price as the investors may choose to sell what they've earned.
To prevent that undesired situation WEEB uses dual burning mechanisms.

1. Transfer burn which has a constant burn rate and is applied on every transaction except sell transactions and transfers from contracts.
1. Sales burn which has a variable burn rate and is applied only on sell transactions.

The token's price is periodically tracked by the built-in price oracle and as the current price deviates from the tracked time-weighted average price (TWAP), either above or below it, the sales burn rate proportionally increases to make selling less attractive and to favor holding.

[Insert price (TWAP) vs sales burn rate graph here]

Investors are known to sell as the price appreciates or panic sell as the price depreciates. Those are the moments where sales burn rate increases. The higher the difference of the current price from the TWAP the higher the sales burn rate becomes.

When the price depreciation increases the block reward increases proportionally to incentivize holding with an increased yield.

A calm investor may chose to wait for the next price snapshot(s) where the difference between the current price and TWAP becomes lesser and sales burn rate decreases.

&nbsp;

### Burn Rebates

The accounts holding certain amount of tokens have burn rate rebates, both in transfer burn and in sales burn rates.
This incentivizes investors to buy and hold more tokens by matching the dynamic minimum required amount which is a percentage of the dynamic supply.

&nbsp;

Which burn rate?
if sender is contract or sender is nonburnable the burn rate is 0;
totalSupply can not go below minimumSupply,
if (totalSupply() > minimumSupply) {
    burn;
} else {
    burn rate is 0;
}
Burns can not decrease totalSupply below minimumSupply.


    function _burnRateOf(address recipient) internal view override returns (uint256) {
        // Is sell event?
        if (_isInflationRegulated() && recipient == liquidityPair) {
            return _currentSalesBurnRate();
        } else {
            return transferBurnRate;
        }
    }

    function _checkedBurnAmountOf(
        address sender,
        address recipient,
        uint256 amount
    ) internal view returns (uint256) {
        // Since contracts don't earn rewards they should also don't burn.
        // If sender is marked non burnable or if the transaction originated from an address marked non burnable (like a _msgSender() executing a farm contract method which calls transferFrom where sender is farm contract).
        if (sender.isContract() || nonburnables[sender] || nonburnables[_msgSender()]) {
            return 0;
        }

        return _burnAmountOf(recipient, amount);
    }


1. Non-custodial yield farming.

    Holding your tokens in your wallet is enough to generate passive income.

1. Dynamic emission.

    Reward goes up when sells increase to incentivize holding.

1. Fixed transfer burn rate. -Constant pressure on inflation.
1. Dynamic sales burn rate. -Incentivizes holding by increasing sales burn rate on high volatility.
1. Rebate on burns. -Higher balances burn less. Big fish friendly.