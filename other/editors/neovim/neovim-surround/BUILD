prepare_install &&

INSTPTH=/usr/share/nvim/runtime

mkdir -p $INSTPTH/{plugin,doc} &&
install -Dm644 doc/* $INSTPTH/doc/ &&
install -Dm644 plugin/* $INSTPTH/plugin/ &&
install -Dm 644 README.markdown -t /usr/share/doc/$MODULE

