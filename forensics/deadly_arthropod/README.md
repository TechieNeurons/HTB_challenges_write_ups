1. We get a pcap with USB in it
2. Take a look at how to transform usb in letters : https://github.com/carlospolop-forks/ctf-usb-keyboard-parser
3. the data is in ``` usbhid.data ```, the final command was :

``` bash
tshark -r deadly_arthropod.pcap -Y 'usb.data_len == 8' -T fields -e usbhid.data | sed 's/../:&/g2' >> usbhid_keys.txt

# Then

python ./ctf-usb-keyboard-parser/usbkeyboard.py ./usbhid_keys.txt # If error delete first blank line in the txt file
```

4. Flag !