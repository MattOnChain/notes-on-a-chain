# BRC-20

BRC-20 are alt-coins created and traded on the Bitcoin blockchain. Most have zero utility and are traded based on pure speculation that they will go viral and see market price increases as they trend.

Unlike $BTC, the native currency of Bitcoin, BRC-20 is a protocol that derives the balance of alt-coins from the state of Ordinal inscriptions.

BRC-20 tokens are transacted on-chain as any Ordinal. The content of each BRC-20 Ordinal is a JSON string in the format specified by the protocol.

BRC-20 functions include the following:
- Deploy: Create a BRC-20 token while defining parameters such as the 4-character ticker symbol, maximum supply, and the limit that can be minted in a single mint inscription.
- Mint: Mint an amount of a previously deployed BRC-20 token. Mints provide a balance only to the first owner of the Mint ordinal. **You cannot move a balance of BRC-20 by sending a Mint token.**
- Transfer: Transfer an amount of BRC-20 token. **Transfers only work once.** They must be inscribed into an address holding a valid balance and then be sent to another address as a means of transferring the balance to the new address. The “used” Transfer Ordinal continues to exist but is invalid and cannot be reused.  A new Transfer token must be minted and sent in order to send a balance amount from the new holding address. **When minting Transfers, consider padding the Ordinal (ex. to 8,500 sats) as you will need to spend fees to send the Transfer Ordinal.**

For illustrative purposes, the scenario below lists the actions taken as John and Jane mint a BRC-20 ticker and John subsequently transfers half his balance to Jane.

|Name   |Action                     | John’s Balance| Jane’s Balance|
|-------|---------------------------|---------------|---------------|
|John   |Inscribe Deploy		        |              0|               |
|John   |Inscribe Mint 1,000	      |          1,000|               |
|Jane   |Inscribe Mint 2,000	      |               |          2,000|
|John   |Inscribe Transfer 500      |     	   1,000|     	        |
|John   |Send Transfer 500 to Jane	|            500|		       2,500|

## Marketplaces & Wallets

Various sites and wallets facilitate the inscribing process so that the above may be handled as a function of buying and selling when in fact what is occurring is Transfer tokens are being inscribed and sent as a means of moving the balance from one wallet (seller) to another (buyer).

## Returning a Transferable Balance to Your Available Balance
If after inscribing a Transfer token (and before sending it) you want to change a Transferable balance back to your Available balance, you must transfer the valid Transfer to yourself.

## Checking the Balance
At any point, you can use UniSat to [check the balance of BRC-20](https://unisat.io/brc20) in an address.

## JSON Content
The following are examples of the text strings to be inscribed on BRC-20 Ordinals for each of the three operations.

```
{ 
"p": "brc-20",
"op": "deploy",
"tick": "ordi",
"max": "21000000",
"lim": "1000"
}

{ 
  "p": "brc-20",
  "op": "mint",
  "tick": "ordi",
  "amt": "1000"
}

{ 
  "p": "brc-20",
  "op": "transfer",
  "tick": "ordi",
  "amt": "100"
}
```

