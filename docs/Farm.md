# How do the Farms work generally?

WEEB token is the main actor in the Weeb Finance ecosystem.
Due to it's intrinsic staking and inflation regulation mechanisms it allows for new and unique products to be created, Weeb Farms being one of them.

Unlike traditional farms which are mainly staking pools of different assets with distinct and static emission rates (multipliers) cause rapid increases in token supplies where teams periodically do buybacks and token burns to lift prices by limiting the supply of tokens available for sale, Weeb Farms evolved around the WEEB token's built in staking and inflation regulation mechanisms provided a more controlled emission and buyback methods to be achieved thus arised to hybrid farms which are combination of classic farming and lending mechanisms.

**How is this happening?**

An investor deposits a token or a liquidity pair token to a farm of their chosing (collateral part).

The protocol then calculates the WEEB token equivalent value of that deposited token amout through decentralized exchanges (DEX) where their liquidities reside and credits/mints that WEEB token amount to the investor's account (lending part).
Once obtaining the WEEB token the investor starts to generate yield right away.
This action, temporarily increases the supply (temporarily becasuse when lender returns the credit supply will decrease) and allows infaltion to be regulated automatically and dynamically from a single place unlike classic farms which don't have such mechanisms.
WEEB token's built-in inflation regulator increases/decreases emissions and burns under certain conditions to balance the price.

Since the credit amount is calculated at the deposit time and prices are in a constant fluctuation the investor may be holding more or less WEEB tokens for their deposit at a later time.
This is a situation which must be rebalanced for the investor to increase their earnings or for the protocol to not be abused by generating more yield than it should.

Due to the reason that the investor may want their deposited/collateral asset back at a later time the credited WEEB amount is locked in investor's acount and can not be traded but increases the investor's balance thus making them generate more yield per tokens held.
When the credited WEEB amount is returned their deposited asset is freed and the credited WEEB amount is burned to reduce the supply.



---
&nbsp;

## **(This part is too much information and can be used while app workings are explained.)**

Let's dive deeper.

There are two possible scenarios where the relative price between deposited token and WEEB changes;

1. **The deposited token's price increases more than the WEEB's price**:

    In that situtation an opportunity windows is present for the investor to increase their credited WEEB by rebalancing.
    Protocol burns the existing credited amount and credits/mints more WEEB to the investors wallet.
    The increased amount increases the investor's share in the pool and the yiled goes up.

2. **The WEEB's price increases more than the deposited token's price**:

    The investor has two options;

    a. To rebalance and update their credited WEEB to a lower value and continue with a lower yield and staying on the safe side.

    b. To not rebalance and take advantage of the imbalanced credit which he optained at deposit time till the liquidation limit or beyond.

    Each pool has a limit to where the investor can take advatage of the imbalanced credit. Beyond that limit the investor's deposit can be liquidated by being converted to WEEB at the current exchange rate and transferred to their wallet unlocked (tradable).

    The liquidation process is not automated. A third party can liquidate any under allowed level inbalanced investment by constantly monitoring the pools to generate passive income.
    This liquidation process is also beneficial to the investor if their deposited asset is constantly losing value. By liquidation they are switched to a better performing asset.

&nbsp;

Let's set an example:

The investor deposits 100 X tokens to the X farming pool where the liquidation rate is 30% and liquidator fee is 1%.
At the deposit time the echange rate between X and WEEB tokens is 1:1.
The investor is credited 100 WEEB tokens and the liquidation level for the transaction is set to be 70 WEEB tokens.

1. The price of X token appreciates and the echange rate between X and WEEB tokens becomes 1:2.
For every X token investor gets 2 WEEB tokens. It's in the advantage of the investor to rebalance and receive 200 WEEB tokens for their 100 X tokens.

2. The price of WEEB appreciates and the exchange rate between X and WEEB tokens becomes 1.25:1.
For every X token investor gets 1/1.25 = 0.80 WEEB tokens.
If the investor chooses to rebalances their investment they will get 80 WEEB tokens which is less than what they're already holding.
The investor chooses to not rebalance thinking the price may rocover and takes advantage of the allowed limit.
At a later time the exchange rate between X and WEEB tokens becomes 1.50:1.
For every X token investor gets 1/1.50  = 0.67 WEEB tokens which is under the liquidation level which was set to be 70 WEEB tokens at the time of the deposit.
Now, the investor is open to liquidation. If they chose to rebalance and continue with 67 WEEB tokens they are safe. If they choose not to rebalance a third party can liquidate them anytime. Their deposit will be converted to WEEB at the current rate which is 67 WEEB. The liquidator will get 1% of that which is 0.67 WEEB and the investor will receive 67 - 0.67 = 66.33 WEEB tokens unlocked in their account.
When the investor liquidates themself the liquidator fee is not deducted and they receive the full amount of 67 WEEB tokens.
