# Sat Hunting

Bitcoin has periodic events that create a system of rarity for sats:
- Common: Any sat that is not the first of its block
- Uncommon: The first stat of each block (every 10 minutes)
- Rare: The first sat of each difficult adjustment period (roughly every 2 weeks)
- Epic: The first sat of each halving cycle (roughly every 4 years)
- Legendary: The first sat of each cycle (roughly every 24 years)
- Mythic: The first stat of the genesis block (once, the first block)

Sat hunting is the process of reviewing individual sats in hopes of finding something other than Common sats.

Collectors may desire sats based on any criteria deemed interesting. Examples include:

- Vintage: Sats mined in the first 1,000 blocks
- Events: Sats tied to a historical event such as those from Block 78, the first Bitcoin transaction sent from Satoshi Nakamoto to Hal Finney.
- Sat names: Using a modified base-26 encoding (numbers are converted to letters) each satoshi has a unique name value. Some names are more interesting than others.
- Sat number or name palindromes (reads the same backward as forward).


> Reference: @ItsFrankenSense shared a [thread on how to sat hunt](https://twitter.com/itsfrankensense/status/1634186660220121088?s=61&t=ge5cRPQmLIF1TEYO9qnLrg) and later followed it up with a [thread on how to extract sats](https://twitter.com/itsfrankensense/status/1639202586074152969?s=61&t=WKdE58PhrANZt59nGyyk1A).


## Part 1: The Hunt

1. Move $BTC from an exchange to Sparrow
2. Under UTXOs, right-click on the Output value of the received BTC and select Copy Transaction Output
3. Paste the value into the search at Ordinals.com
4. View the many Sat Ranges
5. A range with an Uncommon sat will appear in a different color
6. Look for shorter range numbers (fewer characters when scanning down the list) and click the shorter ones to find vintage sats

> As an alternative to manually reviewing the sat ranges on Ordinals.com, tools like [Sat Hunter Pro](https://hunter.raresatsociety.com/) and [Sating.io](https://sating.io/) provide a simple UI to identify interesting sats.

## Part 2: The Extraction

1. Copy and paste the list of sat ranges from Ordinals.com into a plain text formatted text file. This serves to strip the HTML formatting before pasting the data into Excel.
2. Copy and paste the ranges from the text file into Excel

> Important: Excel cannot properly handle the large values of sat ranges and this results in bad math when attempting to subtract the start and end range values. To work around this problem, use formulas to work with only the last 10 digits on each side of the range (=right(text, num_chars)).

3. Create formulas to derive the number of sats in each range
4. Add up your results and confirm this matches the Value as shown atop Ordinals.com for this transaction output. This confirms you accurately calculated the number of sats in each range.
5. Derive the number of sats before the range you want to extract by adding up all the rows above the range containing the sat you will keep.
6. In Sparrow, select the UTXO and click to Send
7. You will create three parts to this one transaction
   1. Part 1 (to Exchange): The total number of sats calculated when adding all the ranges before the desire sat. Label this like '1. Send back to exchange'.
   2. Part 2 (to Keeper wallet): 10,000 sats (this includes the rare sats plus padding). Label this like '2. Keep Uncommon sat'.
   3. Part 3 (to Exchange): Hit the max button for the remaining sats in the UTXO. Label this like '3. Send remainder back to exchange'.

> Caution: After creating the transaction but before broadcasting it, make sure the order of transactions outputs (right side of transaction diagram) show as desired. Likely it will not be in the desired order because Sparrow randomizes this. If the order is wrong, close the transaction and go back to click Create Transaction again. Do this until the orders is correct. **Only then should you sign and broadcast the transaction.**

> Note: Sat ranges include the first sat in the range and exclude the last sat.  Meaning when viewing a single range on Ordinals.com, the last sat is not part of that group/range of sats.