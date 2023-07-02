# Ord Setup (Mac)

Cargo presents a simple method for installing Ord.  While we did not try this, instead of using Cargo you may be able to install the latest pre-built binary from Terminal with the following command.

```
curl --proto '=https' --tlsv1.2 -fsLS https://ordinals.com/install.sh | bash -s
```

The method chosen below uses Cargo to install Ord.

## Install Cargo with RustUp

Ord is written in Rust. RustUp installs the required Rust language and Cargo package manager. Commands below are to be used in Terminal.

   1. Go to https://rustup.rs and copy the command and paste it to run in Terminal
   2. Where you are presented an option and one is shown with “(default)”, just press enter at the prompt to use that default
   3. Add Cargo to the path
      1. If the following command returns "cargo not found", that confirms Cargo is not already in the shell. Then proceed to next command (source...)
```
which cargo
```
```
source "$HOME/.cargo/env"
```
   4. Try again to confirm Terminal now finds Cargo
```
which cargo
```

   5. Close Terminal and reopen it


## Install Ord

1. Start your Bitcoin node (Open Bitcoin QT from your Applications folder)
2. In terminal, enter the install command
```
cargo install ord
```

3. Once Ord is installed, the following command should reveal that Ord is installed by indicating its location. Alternately you can use the command 'which ord'
```
ord --version
```
> Note for reference: The Ord binary is stored in /Users/yourusername/.cargo/bin

## Build the Ord Index
1. In the bitcoin.conf file add the following entry
```
server=1
```
2. Save and close the bitcoin.conf file
3. Restart Bitcoin Core

> The default location for the Ord index is ‘/Users/yourusername/Library/Application Support/ord’ but in this setup it will be created on an external drive. For performance reasons, an SSD drive is recommended. SSD is not explicitly required of course, but with it you will see dramatic speed improvement during indexing and the increased performance will reduce the number events resulting in a corrupt index file.
>
4. On the external drive, create a folder called 'Ord'
5. In the new folder, add a plain text empty file called ‘index.redb’
   1. Or [download an index file](https://45.128.27.75/) as linked from a posting in [The Ordicord Discord server](https://discord.com/channels/987504378242007100/1083363982963908640) and place this as your starting index file
6. Start building the index with the following command where the additional arguments are required to point to the external hard drive location of the index.redb and cookie.index files

> Note: If you did not move the Ord index from its standard location, you do not need the --index argument
   
```
ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie index
```

7. Wait as long as it takes for the index build to complete
8. In Terminal, use CTRL-C at any point to stop the process (it can be restarted later)


## Start the Ord Server

1. Before starting Ord Server, create a backup of the ord index in case file ever gets corrupted
> Important: You will want to routinely backup your Ord index file as it will become corrupted at times. When that occurs (as is indicated when the Ord server starts throwing up errors) you simply delete the index.redb file and replace it with your latest backup. Ord will then rebuild the index from where it left off.

> Note: Ord indexes automatically while running the Ord Server. So the index function (not shown below) is only used as a means to index when not running server.

1. Start Ord Server
```
ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie server
```

2. In the browser go to http://localhost to access your local host of Ordinals.com

> Congratulations. Bitcoin Core and Ord are fully installed and functioning. You always need Bitcoin running before starting Ord. And at any time, you can use CTRL-C to stop the Ord server and restart it.

> Reference: [Hell Money Podcast: How to Make an Inscription Part 1](https://www.youtube.com/watch?v=zXlvkOSVM9M&t=1s)

## Create an Ord Wallet & Inscribe

Inscription services make it very easy to inscribe anything. However, for more advanced inscription needs such as inscribing on an Uncommon sat you are holding, you may need to inscribe from your Ord server. The following steps provide the basic foundation for inscribing from Ord. 

### Create the Wallet
1. Kill the Ord server with CTRL-C
```
ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie wallet create | pbcopy
```
> Note: Add ‘ | pbcopy’ to the end of the command if you want the resulting seed phrase to automatically be copied to the clipboard

2. Temporarily paste the seed phrase so that you can later save it as desired (ex. print it to hardcopy and lock it in your safe)

### Create an Inscription
1. To get a fresh address
```
ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie wallet receive
```
2. Send BTC to this address as will be need to pay inscription transaction fees assessed by the network.
3. Ord will play a sound when the payment transaction is confirmed. Wait for Bitcoin QT to show the updated available balance. Or go to [mempool.space](https://mempool.space) and paste the address to see the status of the transaction.

4. Confirm the wallet balance
``` 
ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie wallet balance
```
5. Inscribe while setting the fee rate to an appropriate level as can found on [mempool.space](https://mempool.space)
```
ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie wallet inscribe /Users/yourusername/Desktop/OrdinalsTest.txt --fee-rate 35
```
> This test is to create a text-based Ordinal with the contents of OrdinalsTest.txt as the body of the Ordinal. For a higher fee you can instead inscribe anything (ex. .webp file, which is an ideally compressed image).

6. Wait for the commit and reveal transactions to complete
7. Note your inscription ID is shown in the output. You can paste that into Ordinals.com or your Ord page to view the inscription
8. The inscription is sent to a new address in your Ord wallet

> Note: To do a dry run (perhaps to see the total cost before actually broadcasting the transaction)

```
ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie wallet inscribe /Users/yourusername/Desktop/OrdinalsTest.txt --destination bc1addresstoreceivetheinscription1234 --fee-rate 35 --dry-run
```
9. To see your inscriptions
```
ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie wallet inscriptions
```

10. Transfer the new Ordinal to a keeper wallet as desired. For the safety afforded with its coin-control features, this is most easily done from Sparrow after you import your Ord wallet using the seed phrase. And if after importing the Ord wallet into Sparrow, Sparrow does not reveal your inscription, try changing Sparrow's Gap Limit setting (Wallet > Advanced > Gap Limit) from the default to something like 250. This setting tells Sparrow how many empty address to find before it stops scanning them for transactions.

>Reference: [Hell Money Podcast: How to Make an Inscription Part 2](https://www.youtube.com/watch?v=LXrUu8WOrHo)


## Other Commands

```
ord --help

ord wallet -help

ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie wallet balance
```