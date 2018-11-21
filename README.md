### Run the code

Plug your phone into your computer.

Build and run the code

    $ cd ~/nfcRead
    $ cordova run

### NFC Code
**www/js/index.js**

    nfc.addNdefListener(
        function (nfcEvent) {
            var tag = nfcEvent.tag,
                ndefMessage = tag.ndefMessage;

            // dump the raw json of the message
            // note: real code will need to decode
            // the payload from each record
            alert(JSON.stringify(ndefMessage));

            // assuming the first record in the message has
            // a payload that can be converted to a string.
            alert(nfc.bytesToString(ndefMessage[0].payload).substring(3));
        },
        function () { // success callback
            alert("Waiting for NDEF tag");
        },
        function (error) { // error callback
            alert("Error adding NDEF listener " + JSON.stringify(error));
        }
    );

### Scan a NDEF tag

Scan an NDEF tag with your phone. If you need to put data on a tag, try writing a plain text message to a tag with [NXP Tag Writer](https://play.google.com/store/apps/details?id=com.nxp.nfc.tagwriter).