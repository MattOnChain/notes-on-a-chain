# Sparrow

> Reference: [Ordinals.com](https://docs.ordinals.com/guides/collecting/sparrow-wallet.html) guide details how to setup a Taproot (P2TR) wallet in Sparrow for receiving Ordinals.

## Understanding UTXOs

Each time you receive sats, a new UTXO (Unspent Transaction Output) is created. Each UTXO can be managed separately. When sending an asset, you will typically select one UTXO.

Sparrow wallet is unique in the level of coin-control it provides. This is the detailed view of UTXOs and the granular ability to control which are spent (sent).

## Freezing UTXOs

> Important: It can be tricky to send Ordinals from Sparrow. As a means of protecting Ordinals from being accidentally lost when intending to send a specific asset, you should get in the habit of freezing all UTXOs as soon as transactions are confirmed.

UTXOs can be frozen and unfrozen as a way to protect them from being included with other UTXOs when sending Ordinals from Sparrow. 

To freeze and unfreeze a UTXO, simply right-click the Transaction Output and select the appropriate action.

## Viewing Received Inscriptions
Completed (confirmed) transactions can be viewed in the Transactions tab. And once confirmed, you can view your inscription by starting on the UTXO tab.

1. From the UTXO tab, locate the UTXO labelled to contain the desired Ordinal
2. Right-click on the Output value and select Copy Transaction Output
3. Go to [Ordinals.com](https://ordinals.com), paste the Transaction Output in the Search bar and search to view the contents of the UTXO.
   1. If this is a valid Ordinal, the contents (i.e. image) will be displayed
4. Click on the image to view Inscription number, ID and other values

## Inspecting an Inscription Before Sending

Before sending an Ordinal, it is wise to review a few elements to ensure it is safe to send. To do this, view the inscriptions on [Ordinals.com](https://ordinals.com) and check that:

1. The output identifier matches the ordinal identifier
2. The offset is 0 (this indicates the inscription is properly located on the first sat in the UTXO)
3. The output value has enough sats to cover the transaction fee. Note that if more sats are required, you will need to Pad the UTXO as explained in the [Padding](./padding.md) section of this document.

## Increasing the Fee to Speed Up the Transaction
1. Under Transactions, locate the Unconfirmed transaction you want to speed up
2. Right-click and choose "Replace Fee"
3. Set the new fee
4. Create, sign, and broadcast the transaction

## Connecting Sparrow to Your Node

This assumes you are running a Bitcoin QT on your home network.

1. Add 2 entries to the bitcoin.conf file in the Bitcoin QT datadir (in this case, an external HD named "Bitcoin")
```
rpcbind=0.0.0.0
rpcallowip=192.168.1.20 (IP address of client machine)
```
2. Settings > Server > Edit Existing Connection: Change from Public to Bitcoin Core
   1. If Sparrow and Node are on same machine, leave URL as 127.0.0.1:8332.
   2. If Sparrow is on a machine separate from your node, enter the IP address of the node's host machine. (i.e. 192.168.1.47:8332)
3. Under Data Folder, enter the host machine’s path to where your blockchain data is stored (i.e. /Volume/Bitcoin/Bitcoin)
4. Under User/Pass enter the User and Password found in the .cookie file used by Bitcoin Core (found in the Bitcoin QT datadir external HD)

> Note: The .cookie file is a temporary file created each time Core is started.  Therefore, the password entered in Sparrow must be changed any time Bitcoin Core was restarted.
5. Test Connection

## Sparrow Public Server
The default public server upon setup is electrum.bitaroo.net

## Importing Xverse's Ordinals Wallet Into Sparrow

1. File > New Wallet
2. Give it a name like ‘Xverse (Ordinals)’
3. Script Type: Taproot (P2TR)
4. Under Keystore: New Or Imported Software Wallet
5. Mnemonic Words: Use 12 Words
6. Paste Seed Phrase
7. Click Create Keystore (Note: The Derivation Path should show as m/86'/0'/0')
8. Click Import Keystore
9. Click Apply
10. Set Password as desired


