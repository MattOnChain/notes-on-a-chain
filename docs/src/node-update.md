# Update Bitcoin Node to a New Release (Mac)

## Update Bitcoin QT (GUI)
1. If it's running, shut down Ord server.
2. If it's running, shut down Bitcoin QT.
3. Go to [Bitcoin Core](https://bitcoincore.org/en/download/) and download the Mac .dmg of Bitcoin Core (select ARM if your Mac has an M1 or M2 chip)
4. Open the downloaded .dmg file and copy the Bitcoin application to your Applications folder while overwriting the previous version.
5. Run the Bitcoin app from your Applications folder.

> Note: The first couple of times you try to open the newly installed app, you will need to go to Settings > Privacy & Security to allow the app.

## Update Bitcoin Daemon (bitcoind)

1. If it’s running, shut down Ord server.
2. If it’s running, shut down Bitcoin QT.
3. In Terminal, run the following to confirm the currently installed version
```
bitcoind -version
```
4. If it’s running, shut down bitcoind.
5. In Terminal, run the following command.
```
brew update && brew upgrade 
```
6. Navigate to Go > Home > Library > Application Support > Bitcoin and open the bitcoin.conf file to make sure the contents look appropriate (you may be missing server=1 and that’s okay).
```
datadir=/Volumes/Bitcoin/Bitcoin
txindex=1
server=1
```
7. In terminal, run the following to confirm the update has been applied.
```
bitcoind -version
```
8. In terminal, start bitcoind to confirm it functions
```
bitcoind -datadir=/Volumes/Bitcoin/Bitcoin
or if you created the alias
bitcoindm 
```