## GeniProject-WebCaching
GeniProject of Boston University CS655 fall 2019

# step 1 -- reserve rspec from Geni
use the rspec in my repository
# step 2 -- some basic configurations on client and cache nodes
on client node, run
```
  sudo apt-get update
  sudo apt-get install python-pip
  pip install requests
  pip install matplotlib
```
on cache node, run
```
  sudo apt-get update
  sudo apt-get install trafficserver
  cd /var/run
  sudo mkdir trafficserver
  cd /etc/trafficserver/
  sudo vi records.config
```
change the two attributes of records.config to the following, to set up a forward proxy. It by default uses port 8080.
```
  CONFIG proxy.config.url_remap.remap_required INT 0
  CONFIG proxy.config.reverse_proxy.enabled INT 0
```

# step 3 -- run experiment without cache
on client node, upload withoutCache.py and run it.
```
  python withoutCache.py
```
a graph called withoutCache_timecost_vs_delay.png will be generated in the same folder.
# step 4 -- run experiment with cache
on cache node, run the following command to start the cache server.
```
  cd /usr/bin
  sudo ./traffic_server start
```
(here I add 200 ms for example) you can add a delay on cache server to outer network by
```
  sudo tc qdisc add dev eth0 root netem delay 200ms
```
remember to remove this setting if you want to add another delay. Remove the existing delay setting by
```
  sudo tc qdisc del dev eth0 root netem
```

Now upload withCache.py to client node and run it
```
  python withCache.py
```
