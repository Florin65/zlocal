OPTS+=" --sbindir=/usr/bin"

OPTS+=" --enable-email \
        --enable-fancydm \
        --enable-lfs \
        --enable-orig-ip \
        --with-zlib \
        --with-logdir=/var/log/dansguardian \
        --with-piddir=/var/run/dansguardian"

if in_depends $MODULE clamav; then
  DGUSER="clamav:clamav"
  OPTS+=" --with-proxyuser=clamav --with-proxygroup=clamav"
else
  add_priv_user dansguardian:dansguardian
  DGUSER="dansguardian:dansguardian"
  OPTS+=" --with-proxyuser=dansguardian --with-proxygroup=dansguardian"
fi &&

default_build &&

# Be kind and enable clamav in config
if in_depends $MODULE clamav; then
  sedit "/^#contentscanner.*clamdscan\.conf.*/ s;^#;;" /etc/dansguardian/dansguardian.conf &&
  sedit "s;^#clamdudsfile.*;clamdudsfile = '/tmp/clamd';" /etc/dansguardian/contentscanners/clamdscan.conf
fi &&

[ -d /var/log/dansguardian ] || mkdir -p /var/log/dansguardian &&

if module_installed systemd; then
  mkdir -p /run/dansguardian
fi &&

install -D data/scripts/dansguardian /etc/logrotate.d/dansguardian &&

devoke_installwatch &&
chown -R ${DGUSER} /var/log/dansguardian
