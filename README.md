# influxdb-grafana

## i want you to read, very very carefuly 

checkpoint :
- [x] install influxdb2
- [x] install telegraf
- [x] install grafana
- [x] configure influx-server
- [x] connect influxdb to grafana dashboard
- [ ] connect and create alerting on grafana

ps:
all of these config above require sudo/root to execute

## install influxdb

download gpg key for repo
```
wget -q https://repos.influxdata.com/influxdata-archive_compat.key
```
add gpg to your server
```
echo '393e8779c89ac8d958f81f942f9ad7fb82a25e133faddaf92e15b16e6ac9ce4c influxdata-archive_compat.key' | sha256sum -c && cat influxdata-archive_compat.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg > /dev/null
```
add into trusted gpg
```
echo 'deb [signed-by=/etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg] https://repos.influxdata.com/debian stable main' | sudo tee /etc/apt/sources.list.d/influxdata.list
```
update your repo, and install
```
apt update && apt install influxdb2 influxdb2-cli
```
inspect influxdb and enable it
```
systemctl start influxdb
systemctl is-enabled influxdb
systemctl status influxdb
```

## Install telegraf
download gpg
```
wget -q https://repos.influxdata.com/influxdata-archive_compat.key
```

```
echo '393e8779c89ac8d958f81f942f9ad7fb82a25e133faddaf92e15b16e6ac9ce4c influxdata-archive_compat.key' | sha256sum -c && cat influxdata-archive_compat.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg > /dev/null
echo 'deb [signed-by=/etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg] https://repos.influxdata.com/debian stable main' | sudo tee /etc/apt/sources.list.d/influxdata.list
```
update and install
```
apt update && apt install telegraf
```
check status
```
systemctl status telegraf
```
if error, don't worry, just configure the .conf file, but you should configure it later after accessing and configure influxdb dashboard

## Install grafana

install software that required for grafana

```
apt install gnupg2 software-properties-common -y
```
create folder keyrings for grafana
```
mkdir -p /etc/apt/keyrings/
```
download the keyring
```
wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor > /etc/apt/keyrings/grafana.gpg
```
add it into repo
```
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | tee /etc/apt/sources.list.d/grafana.list
```
update and install the packages
```
apt update && apt install grafana-server -y
```
enable and check status 
```
systemctl status grafana-server
systemctl enable grafana-server
```

## Configure influx-server

just watch my [video](https://www.mediafire.com/file/v4icz692ije96fj/2024-06-20_13-47-45.mp4/file)

## Configure telegraf config
file location
```
vim /etc/telegraf/telegraf.conf
```
edit this config, based from your influx-server configuration

![screenshoot image](img/Screenshot%202024-06-20%20150829.jpg)

after that, just restart your telegraf
```
systemctl restart telegraf
systemctl status telegraf
```

## Connect influx to grafana dashboard
just watch my [video](https://www.mediafire.com/file/v4icz692ije96fj/2024-06-20_13-47-45.mp4/file)

## connect and create alerting on grafana
coming soon!
