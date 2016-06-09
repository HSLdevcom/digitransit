## Requirements

## Initialize server

For Ubuntu 14.04 LTS
- add custom apt repositories for openjdk 8 and nodejs
for this run following commands as root. The adding of the repository keys are not added yet in the docs, so there could be a massage of not signed packages during the upate and during the installation
```bash
echo "deb http://ppa.launchpad.net/openjdk-r/ppa/ubuntu trusty main" >> /etc/apt/sources.list
echo "deb https://deb.nodesource.com/node_4.x precise main" >> /etc/apt/sources.list
apt-get update
```
- install depencies of opentripplanner
```bash
apt-get install openjdk-8-jdk-headless
apt-get install nodejs
apt-get install git
apt-get install build-essential
```
- add ppa for maven3 (througth main repository only maven 2 available) install maven 3 (>= 3.1.1 for some dependencies during install of opentripplanner
```
add-apt-repository ppa:andrei-pozolotin/maven3
apt-get update
apt-get install maven3
```
- creating user for installing and running opentripplanner
```bash
adduser digitransit
```
- change to user digitransit and it's homedirectory
```bash
su digitransit
cd
```
- clone opentripplanner
```bash
git clone https://github.com/hsldevcom/opentripplanner
```
- build opentripplanner with maven
```bash
cd opentripplanner
mvn package
```
- create data direcory
```bash
mkdir ~/data/
```
- get openstreetmap graph for your region, for example download it from [bbbike.org Extract service of pbf-files](http://extract.bbbike.org/) and copy it into the data folder in the homefolder of digitransit
- get gtfs plandata for your region (if not available, ask your public transport provider to hand it out to you in a very kindly way) and copy it into the data folder too
- build graph (the first parameter -Xmx is defining the available maximum memory of this java instance. Be shure that this number fits into your machines memory. The default max memory is 256M, but for larger reagions it's reccomanded to put a decend size for not getting some heap errors)
```bash
cd
java -Xmx7500M -jar opentripplanner/target/otp-0.20.0-SNAPSHOT-shaded.jar --build ./data/
```
- create directory for the running instance and copy data into it
```bash
mkdir otp_running_instance
cp opentripplanner/target/otp-0.20.0-SNAPSHOT-shaded.jar otp_running_instances/.
mkdir otp_running_instance/data
cp data/Graph.obj otp_running_instance/data/.
```
- run opentripplanner, give the server your preferred portnumber (here 1234, routed to 80 through a reverse proxy as described below
```bash
java -Xmx2048M -Duser.timezone=Europe/Rome -jar otp-0.20.0-SNAPSHOT-shaded.jar --server --port 1234 --basePath . --graphs data --autoScan --verbose
```
- eventually create reverse proxy on apache (as root user)
```bash
cd /etc/apache2/sites-available/
touch digitransit.conf
```
Add to the created file with your preferred editor the following lines:
```
<VirtualHost *:80>

        ServerName digitransit.localhost
        ServerAlias digitransit.localhost


        ServerAdmin webmaster@localhost

        ProxyPreserveHost On
        ProxyRequests off
        ProxyPass / http://localhost:1234/
        ProxyPassReverse / http://localhost:1234/ 

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
 
</VirtualHost>

```
then activate the new site
```bash
cd ../site-enabled/.
ln -s ../sites-available/digitransit
service apache2 restart
```
- go to your browser and try to access the server trough your URL set in the reverse proxy configuration


## Customize digitransit-deploy

## Build Open Trip Planner graph
- Configure Open Street Map datasource
- Configure GTFS datasources
- Configure other datasources
- Converting other formats into GTFS
- Fitting GTFS shapes onto Open Street Map roads
- Build OTP graph

## Setup digitransit-geocoder
- Configure Open Street Map datasource
- Configure custom datasources
- Build Geocoder database

## Setup digitransit-map
- Build Postgres
- Build Map vector server
- Build Map server

## Setup digitransit-realtime

## Setup digitransit-otp
- configure OTP graph datasource
- configure GTFS-RT datasources
- configure Disruption info datasource

## Setup digitransit-ui
- Configure OTP
- Configure Map tiles
- Configure Real time
- Configure Geocoding
- Customizing UI styles

## Setup load balancing

## Setup docker compose

## Start environment