## GeniProject-WebCaching
GeniProject of Boston University CS655 fall 2019

# step 1 -- reserve rspec from Geni
# step 2 -- some basic configurations on client and cache nodes
on client node, run
···
	sudo apt-get update
	sudo apt-get install python-pip
  pip install requests
  pip install matplotlib
···
on cache node, run
  	sudo apt-get update
  	sudo apt-get install trafficserver
