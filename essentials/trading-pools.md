---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Trading Pools

## Liquidity Pools&#x20;

In order for people to buy some creator token, we place a portion of them into a liquidity pool which works in 2 phases:

1. **Phase 1** of the user pool is the ICO period where the pool launches with 10 million tokens for sale, and $0 USDC at the beginning (so the pool effectively behaves like 1-sided AMM).&#x20;
   * This type of pool is an [offset-curve pool](https://spl.solana.com/token-swap#offset) on Solana.&#x20;
   * The starting price is $0.00010 per token, and it is the same starting price for every creator token. As people purchase the creator token, they fill up the USDC side of the pool (and remove some creator token supply).&#x20;
   * When the USDC liquidity reaches $1000, the pool transition to a 2 sided-AMM (Phase 2).
2. **Phase 2** of the user pool is when the USDC side of the pool reaches $1000 in liquidity, we transition the pool to a normal 2-sided AMM, which behaves like most DeFi trading platform, and where users can provide extra liquidity to earn trading fees.

<figure><img src="../.gitbook/assets/Diagrams (1).png" alt=""><figcaption><p>Overview of the creator token pools on Kaichi</p></figcaption></figure>

Every token begins with the same price of $0.00010, but the price changes depending on the supply and demand for the token. The more people buy, the more the price increases, and vice versa.&#x20;

All trading on Kaichi is non-custodial and all users always keep their funds in their wallets at all time.&#x20;

## Buffered Dynamic Offset Pool

In case some user place large buy order into the pool, and to avoid very large price impact that could be detrimental for them we have designed a new system that acts as an automated OTC provider called the Buffered Dynamic Offset Pool.&#x20;

We know that in crypto people can be quite aggressive in their purchase, for example when a big celebrity launches a token, many users might want to purchase her token with big buy orders, and given the pools start with little supply initially of 10 million tokens, the slippage might hurt them.&#x20;

To solve that we simply add to the initial 10 millions token (Phase 1 during the ICO period) an extra buffer of 40 millions tokens used as an OTC provider for large buy orders, where the price impact pushes the price by more than 10% to provide the users with a better price (getting more tokens for the same amount of USDC) and less slippage — similar to buying via an OTC desk.

The USDC that Kaichi receives from the token sold via the buffer are used to provide liquidity into the pool, therefore making the pool even more liquid and healthier.

Finally, all the USDC earned by the pool and the buffer by the revenue sharing program (as holder of creator token) go directly into the USDC side of the pool. There is no LP token creation so this will increase token price indirectly, rewarding all token holders and provide liquidity to sellers of the creator token.



{% hint style="info" %}
Price impact refers to the impact of a trade on the market, and slippage refers to the difference between the expected price of a trade and the actual price at which it is executed. These two factors can lead to significant losses for traders and can make it challenging to execute large trades.
{% endhint %}
