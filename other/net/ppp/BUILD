add_priv_group ppp &&

default_build &&
make install-etcppp &&

mkdir -p /etc/ppp/{peers,chat} &&

if ! [ -f /etc/resolv.conf ]; then
  touch /etc/ppp/resolv.conf
  ln -f /etc/ppp/resolv.conf /etc/resolv.conf
fi &&

install -m755 $SCRIPT_DIRECTORY/pon $SCRIPT_DIRECTORY/poff /usr/bin &&

if [ ! -e /etc/ppp/peers/isp ]; then
  install -m644  $SCRIPT_DIRECTORY/peers /etc/ppp/peers/isp
fi &&

if [ ! -e /etc/ppp/chat/isp ]; then
  install -m644  $SCRIPT_DIRECTORY/isp /etc/ppp/chat/isp
fi &&

chown -R root:ppp /usr/bin/pppd /etc/ppp &&
chmod 4750 /usr/bin/pppd  &&
chmod 600 /etc/ppp/*-secrets

if module_installed systemd; then
  install -D -m644 $SCRIPT_DIRECTORY/system.d/ppp.service /usr/lib/systemd/system/ppp@.service
fi
