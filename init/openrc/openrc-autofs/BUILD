_install_openrc_initd(){
    install -Dm755 $SCRIPT_DIRECTORY/openrc/init.d/* /etc/init.d/
}

_install_openrc_confd(){
    install -Dm644 $SCRIPT_DIRECTORY/openrc/conf.d/* /etc/conf.d/
}

prepare_install &&

rm -f /etc/init.d/connmand

_install_openrc_initd
