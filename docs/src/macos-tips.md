# macOS Tips

## Create Aliases for Use in Terminal

The below uses zsh shell. Similar steps exist to do the same with bash.

1. Open your zshrc file in Terminal
```
nano ~/.zshrc
```
2. In the zshrc file, create an alias by adding a line in the following format: alias alias_name='command_to_execute' where you replace alias_name with the name you want to give to your alias, and command_to_execute with the command you want to execute when you use your alias.
```
alias ordindex='/Users/yourusername/.cargo/bin/ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie index'

alias ordserver='/Users/yourusername/.cargo/bin/ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie server'

alias bitcoindm='/opt/homebrew/Cellar/bitcoin/24.0.1/bin/bitcoind -datadir=/Volumes/Bitcoin/Bitcoin'
```



3. Save the changes to the zshrc file by pressing Ctrl+O and then Enter
3. Exit the nano editor by pressing Ctrl+X
4. To make the changes take effect, you can either restart your Terminal application, or use the following command to reload zshrc and make your new alias available for use
```
source ~/.zshrc
```

>  With an Alias established, going forward you need to enter only the alias name for Terminal to execute the command you specified in the .zshrc file. As an example, entering 'orderserver' will now start the Ord server while accessing the Ord index file and the Bitcoin QT cookie file as stored on the external drive.