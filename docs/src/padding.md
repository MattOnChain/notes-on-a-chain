# Padding

Using Sparrow, padding UTXOs is useful when you want to add sats to an Ordinal as you may want to do if you will send the Ordinal in a manner that uses its sats to cover the transaction fee.

1. If not already in your Sparrow wallet, send the Ordinal there
2. In Sparrow, label an unused address like "Spendable BTC" and send at least 10,000 sats to this address
3. Under the Receive tab, label a third address like "Padded Bitcoin Punk #1234"
4. From the UTXO tab, click the Ordinal you want pad along with Command+click to also select the UTXO with your Spendable BTC
5. With the two UTXOs selected, click Send Selected
6. From the Send screen, paste the Pay to address, label the transaction like "Pad Bitcoin Punk #1234", and under Amount enter the total amount of sats you want to make up the padded Ordinal (typically 10,000 sats)
7. Slide the fee range as desired while noticing that as you move the fee, Sparrow changes the order of the inputs as shown on the left side of the transaction workflow diagram

> IMPORTANT: Make sure the Ordinal to be padded appears on the top of the left side, leaving the Spendable BTC to be on the bottom. Sparrow will randomly change this order as you change the fee amount. Just keep playing with the fee slider until it represents the speed you want and the transaction diagram shows the Ordinal as the top item on the left side.

8. Click Create Transaction to proceed to view the transaction before Signing and Broadcasting

> IMPORTANT: Make sure the Ordinal is the first item on both the left and right side of the diagram. Sparrow is randomly ordering these items. If they are not ordered correctly, simply close the window to go back and click Create Transaction again. After doing this a few times, eventually they will be in the desired order.

9. Only when the final view of the transaction shows the Ordinal as the top item in both the inputs (left side) and outputs (right side) should you click to Sign and Broadcast the transaction. **If you get this ordering wrong, you will corrupt your Ordinal.**
10. The Ordinal will be delivered with a size of 10,000 sats