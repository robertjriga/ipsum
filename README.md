![Logo](logo.png)

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

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2018-03-03)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
197.231.221.211|exit1.ipredator.se|11
176.10.104.240|tor1e1.digitale-gesellschaft.ch|10
210.13.64.18|-|10
202.137.147.108|ns1.mof.gov.la|10
104.223.123.98|unassigned.quadranet.com|10
221.194.47.236|-|10
200.109.236.50|200.109.236-50.estatic.cantv.net|10
61.153.56.30|-|10
123.59.182.194|-|10
112.161.187.208|-|10
166.70.207.2|this.is.a.tor.node.xmission.com|10
89.234.157.254|marylou.nos-oignons.net|10
5.188.10.179|-|10
159.65.238.215|-|9
222.186.172.48|-|9
112.112.102.38|38.102.112.112.broad.km.yn.dynamic.163data.com.cn|9
119.10.81.250|-|9
39.65.192.179|-|9
80.211.11.250|host250-11-211-80.serverdedicati.aruba.it|9
159.65.232.26|-|9
221.194.47.245|-|9
103.210.135.136|-|9
171.25.193.20|tor-exit0-readme.dfri.se|9
176.10.99.200|-|9
119.249.54.217|-|9
115.238.245.6|-|9
122.225.36.138|-|9
60.173.82.156|-|9
112.161.220.151|-|9
220.191.194.22|-|9
119.10.72.173|-|9
221.194.47.233|-|9
123.150.200.121|-|9
171.25.193.77|tor-exit1-readme.dfri.se|9
110.9.207.72|-|9
27.211.250.235|-|9
88.171.160.112|ari64-1-88-171-160-112.fbx.proxad.net|9
5.188.203.131|-|9
212.21.66.6|tor-exit-4.all.de|9
111.7.177.239|-|9
185.165.31.79|-|9
221.194.44.211|-|9
124.117.241.152|152.241.117.124.broad.wl.xj.dynamic.163data.com.cn|9
149.56.223.241|exit0.liskov.tor-relays.net|9
123.63.186.66|-|9
221.203.75.211|-|9
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|9
115.238.245.8|-|9
115.238.245.4|-|9
66.70.217.179|tor.cusse.org|9
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|9
176.126.252.12|aurora.enn.lu|9
210.121.164.121|-|9
81.29.247.242|int0.client.access.fanaptelecom.net|8
218.156.85.17|-|8
128.31.0.13|tor-exit.csail.mit.edu|8
180.164.50.160|-|8
61.178.220.148|-|8
121.18.238.39|-|8
114.32.31.250|114-32-31-250.HINET-IP.hinet.net|8
122.226.181.167|-|8
122.226.181.166|-|8
159.65.84.56|-|8
217.61.5.246|host246-5-61-217.static.arubacloud.de|8
221.194.47.243|-|8
164.132.51.91|91.ip-164-132-51.eu|8
121.125.11.182|-|8
78.109.23.1|tornode.torreactor.ml|8
39.82.191.151|-|8
218.48.59.189|-|8
118.144.139.217|-|8
171.25.193.25|tor-exit5-readme.dfri.se|8
103.89.91.28|-|8
176.10.104.243|tor2e1.digitale-gesellschaft.ch|8
183.100.116.142|-|8
80.82.70.133|propet.seekkarma.net|8
65.19.167.132|-|8
185.165.31.74|-|8
180.139.138.165|-|8
217.160.107.156|s20835139.onlinehome-server.info|8
221.194.47.239|-|8
66.240.192.138|census8.shodan.io|8
118.89.240.141|-|8
171.25.193.78|tor-exit4-readme.dfri.se|8
183.230.146.26|-|8
89.31.57.5|dreamatorium.badexample.net|8
199.87.154.255|tor.les.net|8
5.254.112.154|lh31138.voxility.net|8
198.20.69.98|census2.shodan.io|8
80.82.77.139|dojo.census.shodan.io|8
222.99.77.250|-|8
121.14.7.244|-|8
71.6.146.186|inspire.census.shodan.io|8
71.6.146.185|pirate.census.shodan.io|8
209.92.176.24|-|8
80.82.64.127|-|8
45.117.82.184|mail.newparadise.com.vn|8
89.248.167.131|mason.census.shodan.io|8
62.210.37.82|62-210-37-82.rev.poneytelecom.eu|8
71.6.158.166|ninja.census.shodan.io|8
121.18.238.125|-|8
173.254.216.66|exit-01a.noisetor.net|8
58.185.176.108|-|8
188.6.164.245|dslBC06A4F5.fixip.t-online.hu|8
139.198.188.137|-|8
59.41.103.97|-|8
63.251.114.119|-|8
210.26.125.35|-|8
58.143.149.190|-|8
202.97.205.78|-|8
69.90.132.92|ip-69-90-132-92.chunkhost.com|8
115.238.245.2|-|8
221.204.249.135|135.249.204.221.adsl-pool.sx.cn|8
51.255.202.66|tor.asmer.com.ua|8
219.147.95.246|246.95.147.219.broad.dq.hl.dynamic.163data.com.cn|8
118.186.36.50|-|8
111.93.180.182|static-182.180.93.111-tataidc.co.in|8
46.10.150.75|46-10-150-75.ip.btc-net.bg|8
109.63.203.91|ip-109-63-203-91.bb.netbynet.ru|8
162.247.73.206|rosaluxemburg.tor-exit.calyxinstitute.org|8
116.255.193.132|-|8
77.247.181.165|politkovskaja.torservers.net|8
77.247.181.162|chomsky.torservers.net|8
212.237.42.200|host200-42-237-212.serverdedicati.aruba.it|8
119.145.21.178|-|8
