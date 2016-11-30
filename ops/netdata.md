# netdata のインストールするぞ!!

## Prepare
sudo apt-get update -yq
sudo apt-get install -yqq curl jq nodejs vim

## Monitoring everything netdata
curl -Ss 'https://raw.githubusercontent.com/firehol/netdata-demo-site/master/install-required-packages.sh' >/tmp/kickstart.sh && bash /tmp/kickstart.sh netdata-all

## Install netdata
git clone https://github.com/firehol/netdata.git --depth=1
cd netdata
sudo ./netdata-installer.sh --install /opt

## Run netdata
/opt/netdata/usr/sbin/netdata

sudo killall netdata
sudo vim /opt/netdata/etc/netdata/netdata.conf
sudo vim /opt/netdata/etc/netdata/apps_groups.conf
sudo vim /opt/netdata/etc/netdata/python.d/mysql.conf
sudo vim /opt/netdata/etc/netdata/python.d/nginx.conf
sudo /opt/netdata/usr/sbin/netdata
