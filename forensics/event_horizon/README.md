1. After extraction we got a lot of evtx file, when evtx always begin with [**chainsaw**](https://github.com/WithSecureLabs/chainsaw) !
2. Let's begin with the easiest command of chainsaw : 

``` bash
./chainsaw_x86_64-unknown-linux-gnu hunt -r rules/ ../Logs -s sigma/rules --mapping mappings/sigma-event-logs-all.yml --level critical
```

3. With this command we see the attacker download a file on github and launch it with the option **InvokeMimikatz**
4. Let's look at everything chainsaw find (previous command without **--level critical**) = TOO MUCH !
5. "low hanging fruit" : 

``` bash
./chainsaw_x86_64-unknown-linux-gnu hunt -r rules/ ../Logs -s sigma/rules --mapping mappings/sigma-event-logs-all.yml | grep 'HTB'
```