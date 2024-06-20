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
if error, don't worry, just configure the .conf file
```

```
