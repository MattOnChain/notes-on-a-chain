# Xverse & Hiro

> Note: While the same seed phrase may be used to import a wallet into both Hiro and Xverse, each solution uses a different [derivation path](./glossary.md) and therefore uses different addresses. That is to say that if, for example, you have $BTC in Xverse (which uses Wrapped Segwit for its Ordinals address) and you import that wallet into Hiro (which uses Native Segwit), Hiro will not provide access to the $BTC because Hiro will not recognize and display the address used in Xverse.

### Speeding Up Transactions Submitted with Xverse

Xverse does not currently support the ability to send a transaction to replace the fee as is required to speed up a transaction stuck in mempool (because the original fee was too low).

However, the transaction can be sped up outside of Xverse.

One method is to use the premium option at [Bitcoin Jumper](https://www.bitcoinjumper.com) to speed up the BTC transaction. This fee-based service will manually add the transaction to be confirmed by a partner mining node. The fee is calculated to be the cost to include the transaction into one of the next blocks and therefore is above the current miner processing rate.

Alternately, you can import the wallet into Sparrow and therein, increase the fee rate. **With the below, the original transaction is replaced with a new transaction to send the funds back to your wallet. At that point you can resubmit the original transaction as desired.**

1. Copy the seed phrase from Xverse and use it to import the wallet into Sparrow
   1. For Xverse, select a Nested Segwit wallet (3...)
   2. For Hiro, select a Native Segwit (bc1q...)
2. In Sparrow, under Transactions, locate the Unconfirmed transaction you want to speed up
3. Right-click and choose Increase Effective Fee Rate
4. Make sure the "Pay to" address is accurate. This should be your BTC address shown in Xverse. This is important as Sparrow may change this.
5. Set the new fee. To derive the fee amount, multiply the current regular fee rate (sat/vB shown on [mempool.space](https://mempool.space)) by 2.5 as this fee needs to be enough to both process this transaction and speed up the original transaction.
6. Create, sign, and broadcast the transaction

> Reference: [How to Speed Up Bitcoin Ordinal Transactions](https://www.youtube.com/watch?v=5wTBkYCn0fk)

## Importing Xverse's Ordinals Wallet Into Sparrow

See [Sparrow Section](./sparrow.md).