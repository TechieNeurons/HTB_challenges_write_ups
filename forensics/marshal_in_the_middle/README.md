1. After extraction we get a pcap, a file secrets.log, a certificate and some log from the tool "Zeek/bro"
2. In the pcap clicked on the first packet and select **"follow -> TCP Stream"** to take a look at the diffferent stream :
- the first one show us some weird HTTP GET
- Stream number 2 show us the command launched as root by the attacker, we can see the attacker exfiltrate data to pastebin.com
3. To decode the TLS communication we will use the secrets.log file, for that :
- go in the **edit** menu then click on **preferences** and find **TLS** in the protocol list 
- Then we select the file **secrets.log** for the **"(Pre)-Master-Secret log filename"** option
4. Now the communication must be decrypted we can add a filter to get only the HTTP packets with pastebin in it, I used this filter **http.host == "pastebin.com"**
7. Just click on the packet on select follow tcp stream to see the data sent to the pastebin, three file was sent, /etc/passwd, /etc/shadow and the database, we will find the flag in the beginning of the database file (between two fake credit card number)
