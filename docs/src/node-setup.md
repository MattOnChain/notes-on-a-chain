# Bitcoin Node Setup (Mac)

> Note: In this Bitcoin Core GUI (a.k.a. Bitcoin QT) setup, the blockchain data is set to be stored on an external drive named ‘Bitcoin’, in a folder named ‘Bitcoin’. With this non-standard configuration, many command line actions require the use of additional arguments to tell the binaries where to find required files. These arguments may not be required if upon installation you accept the default location for your blockchain data.

## Install Bitcoin GUI (a.k.a. Bitcoin QT)
1. Go to [Bitcoin Core](https://bitcoincore.org/en/download/) and download the Mac .dmg of Bitcoin Core (select ARM if your Mac has an M1 or M2 chip)
2. Install Bitcoin Core and run it from the Applications menu
3. Follow the prompts including configuring the data store to use an external drive as desired
> Bitcoin core indexing is intensive with disk i.o. If possible, use an SSD for noticeably better results (faster and fewer corrupt file events). In this example, an external SSD was used.
	
4. Build the full blockchain index
   1. Preferences > Main: Check to Enable RPC server
   2. Open Configuration File: Enter ‘txindex=1’ (without quotes)
   3. Close to save the config file and click OK
   4. Quit Bitcoin Core and restart it.
   5. Wait as many days as it takes to complete the index. This indexing process can be stopped and restarted as desired.

> Note: This process places the bitcoin.conf file in the folder where you told Bitcoin Core to store your blockchain data (i.e. =/Volumes/Bitcoin/Bitcoin). To check the status of the index, open the Console and enter getindexinfo. If the result is "True:, the data is fully sync’d.


## Install the Bitcoin Core Deamon (a.k.a. bitcoind)

>The daemon is a version of Bitcoin Core that can runs in terminal mode, giving you additional capabilities.



1. Install Homebrew
   1. From Terminal, enter ‘Brew’ to confirm ‘command not found’. This indicates Homebrew is not already installed.
   2. Go to [Homebrew](https://brew.sh) and run the install curl command as shown on the site. Note that after installing, Homebrew shows you 2 additional commands to enter into terminal. **These are critical as they will put Brew in your path variable.**
2. Install Bitcoin daemon from Terminal (Utilities > Terminal)

```
brew install bitcoin
```
> Note: Bitcoin binaries are placed in the hidden path /opt/homebrew/opt/bitcoin/bin/ (In Finder, use Command-Shift-Dot to see hidden files and folders).

3. Edit the Config file entry to share the previously acquired blockchain data. This step is done for the unlikely case you have a reason to run the Bitcoin service instead of the daemon.
   1. Navigate to Go > Home > Library > Application Support
   2. On the Go menu hit Option to see the Library folder
   3. At any time use Command-Shift-Dot to see hidden folders (e.g. Library)
   4. If a Bitcoin folder does not already exist, create it under the Application Support folder
   5. Copy the bitcoin.conf file from the blockchain data created earlier to this new folder
   6. Edit the file so that before the txindex=1 entry, the first line of the file reads: datadir=your/path (i.e. datadir=/Volumes/Bitcoin/Bitcoin)
   7. Test daemon with a simple version check command
```
bitcoind --version
or
bitcoin-cli --version
```

4. When needed, run bitcoin daemon from Terminal. The following command is to manually start bitcoind while telling it where to find your blockchain data
``` 
bitcoind -datadir=/Volumes/Bitcoin/Bitcoin
```



## Other Commands

- If instead of on-demand, you want to start bitcoin as a service
```
brew services start bitcoin
```
- Stop bitcoin service
```
bitcoin-cli stop
```
- Restart the service after an upgrade
```
brew services restart bitcoin
```
- Get Blockchain data status where inititialblockdownload=false means the initial download was completed
```
bitcoin-cli getblockchaininfo
```
 
- Help
```
bitcoin-cli -help
```
```
bitcoin-cli -getinfo -help
```

- Get Block Count (Note that [Ordinals.com](https://ordinals.com/clock) also shows the latest block when you hover the cursor over the center of the clock.)
```
bitcoin-cli getblockcount
```
> Important: At this stage you have both the Bitcoin Core GUI and Bitcoin Core daemon installed. These cannot be run simultaneously as they share local blockchain data. The GUI is an easy way to just run the core.  The daemon runs the core while also providing command line capabilities that are helpful, especially when troubleshooting.  Just close/stop one before opening/starting the other.

> Reference: [Hell Money Podcast: How to Make an Inscription Part 1](https://www.youtube.com/watch?v=zXlvkOSVM9M&t=1s)