http://public-yum.oracle.com/repo/OracleLinux/OL6/addons/x86_64/getPackage/docker-0.11.1-22.0.1.el6.x86_64.rpm

echo "export http_proxy=http://www-proxy.us.oracle.com:80/" >> ~/.bashrc
echo "export https_proxy=http://www-proxy.us.oracle.com:80/" >> ~/.bashrc


echo "proxy=http://www-proxy.us.oracle.com:80/" >> /etc/yum.conf

echo "nameserver 172.18.20.13" >> /etc/resolv.conf
echo "nameserver 172.20.100.29" >> /etc/resolv.conf
echo "nameserver 8.8.8.8" >> /etc/resolv.conf


touch /etc/default/docker
echo 'DOCKER_OPTS="--dns 172.18.20.13 --dns 172.20.100.29 --dns 8.8.8.8"' >> /etc/default/docker

sudo HTTP_PROXY=http://www-proxy.us.oracle.com:80/ /usr/bin/docker -d &

