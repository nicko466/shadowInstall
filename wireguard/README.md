

mkdir -p /etc/wireguard 
cp wireguard.conf /etc/wireguard/.

docker run -it --rm cmulk/wireguard-docker:stretch genkeys

qrencode -t ansiutf8 < tunnel.conf
