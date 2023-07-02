# Update Ord to a New Release (Mac)

In this example, Ord 0.5.2 was updated to Ord 0.6.1

1. Determine the current release of your Ord server: 
```
ord --version
```

2. CTRL-C to stop your Ord server
3. Now is a good time to make sure all your backups are up-to-date
4. Download the latest compiled Ord release from [GitHub](https://github.com/ordinals/ord/releases). If on Mac with M1 or M2 processor, choose the AArch tar.gz package
5. Double-click the .gz file to extract its contents
6. Open another Finder window and press Command+Shift+Dot to view hidden files
7. Navigate to where your current Ord binary is located: /Users/yourusername/.cargo/bin
8. Rename the current ord file like ord.052.old
9. Drag the new ‘ord’ binary file to the same folder as the old binary file
10. The following command may prompt macOS with a security warning. If so, go to Settings > Privacy & Security and scroll to find where it says Ord was blocked. Click to Allow Anyway. Keep doing this Version command until you stop getting warnings and it responds to indicate the new version. Alternately you can try to simply right-click on the Ord binary in Finder and then proceed to terminal.
```
ord --version
```

> Note: The upgrade from Ord 0.5.2 to 0.6.1 introduced handling for Cursed Inscriptions. As a result, Ord must build a completely new index file. Therefore, the next step is not typically necessary for a basic Ord upgrade.

11. To force Ord to build a completely new index file, rename the current index.redb file to index.redb.old
12. Run the index command
```
ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie index
```
> Note: As of Ord 0.7.0 you need to add 'run' to the end of the index command.
```
ord --index /Volumes/Bitcoin/Ord/index.redb --cookie-file /Volumes/Bitcoin/Bitcoin/.cookie index run
```
13. Wait as long as it takes for the index build to complete

> This indexing took approximately 1.5 hours while indexing to an external SSD drive.

14.  In Terminal, use CTRL-C at any point to stop the process (it can be restarted later)
15.  When the index build completes, start your Ord server

