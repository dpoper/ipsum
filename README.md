![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of shame (2020-09-20)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
54.38.81.231|ns31251136.ip-54-38-81.eu|10
217.182.192.217|ns3073700.ip-217-182-192.eu|10
104.244.75.53|-|10
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|10
185.220.101.9|-|10
185.165.168.229|-|10
171.25.193.20|tor-exit0-readme.dfri.se|10
64.113.32.29|tor.t-3.net|10
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|10
107.189.10.101|-|9
185.220.101.207|-|9
192.42.116.13|this-is-a-tor-exit-node-hviv113.hviv.nl|9
51.83.139.55|ip55.ip-51-83-139.eu|9
207.244.70.35|-|9
145.239.82.87|relay10f.tor.ian.sh|9
107.189.10.174|-|9
51.77.135.89|ns31066279.ip-51-77-135.eu|9
185.67.82.114|tor-ou.effi.org|9
51.75.144.43|ns3129517.ip-51-75-144.eu|9
62.102.148.69|-|9
62.102.148.68|-|9
185.129.62.62|tor01.zencurity.dk|9
162.247.74.74|wiebe.tor-exit.calyxinstitute.org|9
77.247.181.165|politkovskaja.torservers.net|9
51.15.43.205|tor4thepeople3.torexitnode.net|9
212.47.229.4|-|9
18.27.197.252|wholesomeserver.media.mit.edu|9
209.95.51.11|nyc-exit.privateinternetaccess.com|9
185.220.102.8|185-220-102-8.torservers.net|9
51.83.69.84|welcome-europe.website|9
185.220.103.7|anatkamm.tor-exit.calyxinstitute.org|9
51.75.52.118|ns3130898.ip-51-75-52.eu|9
51.195.148.18|relay2.tor.ian.sh|9
185.220.102.250|tor-exit-relay-4.anonymizing-proxy.digitalcourage.de|9
185.100.87.206|geri.enn.lu|9
185.220.101.134|-|8
51.79.53.134|134.ip-51-79-53.net|8
195.154.179.3|195-154-179-3.rev.poneytelecom.eu|8
185.220.102.247|185-220-102-247.torservers.net|8
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|8
66.70.191.218|tor.0xem.ma|8
162.247.72.199|jaffer.tor-exit.calyxinstitute.org|8
192.42.116.19|this-is-a-tor-exit-node-hviv119.hviv.nl|8
185.130.44.108|tor-exit-se1.privex.cc|8
193.218.118.131|131.118.218.193.urdn.com.ua|8
185.32.222.168|-|8
51.83.139.56|ip56.ip-51-83-139.eu|8
162.247.74.217|perry.fellwock.tor-exit.calyxinstitute.org|8
51.79.86.181|181.ip-51-79-86.net|8
162.247.74.7|korematsu.tor-exit.calyxinstitute.org|8
35.0.127.52|tor-exit.eecs.umich.edu|8
144.217.60.239|ip239.ip-144-217-60.net|8
178.165.72.177|178-165-72-177-kh.maxnet.ua|8
185.220.101.16|-|8
185.220.101.15|-|8
192.42.116.23|this-is-a-tor-exit-node-hviv123.hviv.nl|8
192.42.116.27|this-is-a-tor-exit-node-hviv127.hviv.nl|8
192.42.116.24|this-is-a-tor-exit-node-hviv124.hviv.nl|8
77.247.181.163|lumumba.torservers.net|8
194.180.224.130|-|8
217.170.206.146|-|8
195.206.105.217|zrh-exit.privateinternetaccess.com|8
79.137.79.167|tor-exit.talyn.se|8
162.247.74.201|kunstler.tor-exit.calyxinstitute.org|8
162.247.74.204|billsf.tor-exit.calyxinstitute.org|8
171.25.193.78|tor-exit4-readme.dfri.se|8
185.220.101.8|-|8
104.244.75.153|-|8
51.75.64.187|relay4.tor.ian.sh|8
198.96.155.3|exit.tor.uwaterloo.ca|8
195.206.107.147|-|8
185.220.102.6|185-220-102-6.torservers.net|8
107.189.11.163|-|8
23.129.64.187|-|8
171.25.193.25|tor-exit5-readme.dfri.se|8
144.172.71.182|-|8
23.129.64.100|-|8
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|8
185.220.102.252|tor-exit-relay-6.anonymizing-proxy.digitalcourage.de|8
23.129.64.205|-|8
104.244.74.169|-|8
216.239.90.19|tor-gateway.vif.com|8
54.39.16.73|ns555166.ip-54-39-16.net|8
185.100.87.41|-|8
185.220.101.203|-|8
185.100.87.207|freki.enn.lu|8
128.31.0.13|tor-exit.csail.mit.edu|7
51.79.53.139|139.ip-51-79-53.net|7
188.214.104.146|api.squired.ro|7
185.220.102.244|185-220-102-244.torservers.net|7
185.220.102.245|185-220-102-245.torservers.net|7
185.220.102.240|185-220-102-240.torservers.net|7
185.220.102.241|185-220-102-241.torservers.net|7
185.220.102.242|185-220-102-242.torservers.net|7
185.220.102.243|185-220-102-243.torservers.net|7
185.220.102.249|tor-exit-relay-3.anonymizing-proxy.digitalcourage.de|7
107.189.11.78|-|7
107.189.10.93|exit.tor.gg|7
217.170.205.14|tor-exit-5014.nortor.no|7
89.144.12.17|-|7
104.244.77.95|-|7
192.42.116.14|this-is-a-tor-exit-node-hviv114.hviv.nl|7
192.42.116.15|this-is-a-tor-exit-node-hviv115.hviv.nl|7
193.218.118.130|130.118.218.193.urdn.com.ua|7
185.220.101.215|-|7
93.93.46.180|mwittig.data-expertise.com|7
51.79.86.180|180.ip-51-79-86.net|7
89.236.112.100|tor-jy.effi.org|7
162.247.74.213|snowden.tor-exit.calyxinstitute.org|7
193.228.91.105|-|7
176.10.104.240|tor1e1.digitale-gesellschaft.ch|7
198.100.155.37|vps-8d15e72e.vps.ovh.ca|7
185.32.222.170|-|7
51.79.86.177|177.ip-51-79-86.net|7
51.79.86.175|175.ip-51-79-86.net|7
217.170.206.192|-|7
192.42.116.22|this-is-a-tor-exit-node-hviv122.hviv.nl|7
192.42.116.20|this-is-a-tor-exit-node-hviv120.hviv.nl|7
192.42.116.26|this-is-a-tor-exit-node-hviv126.hviv.nl|7
192.42.116.28|this-is-a-tor-exit-node-hviv128.hviv.nl|7
149.202.238.204|204.238.202.149.fr-sbg.flexcloud.seflow.it|7
162.247.74.202|djb.tor-exit.calyxinstitute.org|7
162.247.74.200|kiriakou.tor-exit.calyxinstitute.org|7
162.247.74.206|rosaluxemburg.tor-exit.calyxinstitute.org|7
209.141.54.153||7
185.220.102.246|185-220-102-246.torservers.net|7
164.132.51.91|91.ip-164-132-51.eu|7
91.250.242.12|-|7
82.221.131.5|-|7
171.25.193.77|tor-exit1-readme.dfri.se|7
185.220.101.3|-|7
104.244.75.157|tor-exit-levy.nucleosynth.space|7
195.254.135.76|-|7
107.189.10.245|tor.kryptosoftwares.com|7
185.170.114.25|this-is-a-tor-node---10.artikel5ev.de|7
185.220.102.4|communityexit.torservers.net|7
23.129.64.180|-|7
173.244.209.5|slc-exit.privateinternetaccess.com|7
185.220.103.8|mariellefranco.tor-exit.calyxinstitute.org|7
66.230.230.230|-|7
217.170.206.138|tor-exit-6138.nortor.no|7
176.10.99.200|accessnow.org|7
85.209.0.253|-|7
145.239.92.26|relay3.tor.ian.sh|7
185.220.102.254|tor-exit-relay-8.anonymizing-proxy.digitalcourage.de|7
185.220.102.251|tor-exit-relay-5.anonymizing-proxy.digitalcourage.de|7
51.68.139.151|151.ip-51-68-139.eu|7
45.95.168.215|maxko-hosting.com|7
45.129.56.200|-|7
95.128.43.164|exit-1.fr.tor.aquaray.com|7
193.239.232.101|-|7
141.98.252.163|-|7
104.244.79.241|lux.tor.stevencampbell23|7
162.247.73.192|-|7
23.160.208.249|relay13f.tor.ian.sh|7
23.160.208.246|relay13f.tor.ian.sh|7
23.129.64.193|-|7
185.220.101.146|-|7
185.220.101.206|-|7
185.220.101.205|-|7
185.220.101.200|-|7
23.160.208.247|relay13f.tor.ian.sh|7
23.160.208.245|relay13f.tor.ian.sh|7
51.254.143.96|96.ip-51-254-143.eu|7
