
# update upgrade

sudo apt update
sudo apt upgrade

# install our best friend docker

sudo curl -sS https://get.docker.com/ | sh


sudo apt install -y docker-compose 

# shadowsocks run

# run a shadowsocks with obfs
docker run -e PASSWORD="mySuperPassword" --restart always -d -p 443:8843/udp -p 443:8443/tcp --name ss_obfs_docker letssudormrf/ss-obfs-docker

# run one simple shadowsocks
docker run  --restart always -dt -p 8478:6443 --name classik mritd/shadowsocks -s "-s 0.0.0.0 -p 6443 -m chacha20 -k mySuperPowerFullPassoword2 --fast-open"

# or install outline manager 
# sudo wget -qO- https://raw.githubusercontent.com/Jigsaw-Code/outline-server/master/src/server_manager/install_scripts/install_server.sh | bash
# check here https://blog.ssdnodes.com/blog/outline-vpn-tutorial-vps/ 

# You must use the Linux kernel version 4.9 or above.

sudo echo "net.core.default_qdisc=fq" >> /etc/sysctl.d/10-custom-kernel-bbr.conf
sudo echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.d/10-custom-kernel-bbr.conf

# check bbr result
# sysctl net.core.default_qdisc
# should return net.core.default_qdisc = fq
# $ sysctl net.ipv4.tcp_congestion_control
# net.ipv4.tcp_congestion_control = bbr
