# Domain Names

## Sats Name System  (SNS)

Sats Names (a.k.a. .sats addresses) is a standard for writing names to Bitcoin using ordinals.

- Addresses can be between 1 and 19 characters long, and use characters a-z, 0-9, -, and _
- Before minting a Sats address, use a site such as [UniSat](https://unisat.io/search) to search to make sure the address has not already been minted
- Go to [UniSat](https://unisat.io/inscribe), [Gamma](https://gamma.io/ordinals) or any preferred inscription service to mint a text ordinal with a JSON string as shown below
 

```
{
"p": "sns",
"op": "reg",
"name": "helloworld.sats"
}
```
> Reference: [About Sats Names](https://docs.sats.id/sats-names/about)

## Bitcoin Name System (BNS)

You can purchase a .btc address at [btc.us](https://btc.us/get/thecloud.btc).

Xverse and Hiro are Stacks-enabled wallets that support the ability to purchase BNS names. You will need $STX to make the purchase.

Each Xverse account can purchase only one .btc address, however you can create additional accounts to purchase additional .btc addresses.

### Inscribing a Zonefile for your .BTC Address

At [BNS.xyz](https://www.bns.xyz/) you can inscribe your .btc name on an Ordinal to establish provenance of the name.

The process will write a copy of your zonefile as a text Ordinal. A zonefile serves to map the .btc name to a wallet address.

## BTC Domains

[BTC Domain](https://app.btcdomains.io/) is attempting to improve upon the Stacks equivalent by offering .btc domain names that are inscribed as formatted JSON text directly on the Bitcoin mainnet, with each domain being a unique inscription.

## Trustless Domains

[Trustless Wallet](https://trustlesswallet.io/) operates on the Trustless Computer chain. It works in cooperation with both the Bitcoin and Ethereum chains as a means to provide smart contact functionality on Bitcoin. For identification, Trustless uses your ETH address as signed through MetaMask while assigning a Bitcoin address to associate with your ETH address.

At Trustless Wallet you can purchase Trustless "Names" with an unknown future utility.

