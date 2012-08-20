以下の方法で作成しましょう。

1. 作業領域を作成します

# mount -t tmpfs -o size=10g,nr_inodes=1000000 none /mnt
# mkdir /mnt/work

2. パッケージを作成します

事前準備として、devscriptsと依存パッケージを入れておいてください

$ cd ~/ubuntu-custom-kd
$ dpkg-buildpackage -uc -us

3. 作業領域でイメージを作成します

# cd /mnt/work
# ubuntu-defaults-image --package ~/ubuntu-custom-kd-*_all*.deb --components main,restricted,universe,multiverse

これで、binary-hybrid.isoができるので、これを焼くなり展開するなりすればOK。

