#Maintainer: Juho Rutila <juho.rutila@gmail.com>
# Copied from mongodb
pkgname=mongodb-bin
pkgver=2.4.3
pkgrel=1
pkgdesc="A high-performance, open source, schema-free document-oriented database."
arch=('i686' 'x86_64')
url="http://www.mongodb.org"
license=('AGPL')
depends=('boost-libs')
optdepends=('libpcap: needed for mongosniff')
provides=('mongodb')
backup=('etc/mongodb.conf')
source=("http://fastdl.mongodb.org/linux/mongodb-linux-$CARCH-${pkgver}.tgz"
        "mongodb.rc"
        "mongodb.conf"
        "mongodb.service"
        )
md5sums=('cdf9cb252e9635c4db1a309f4646aefa'
         'ebc707d3348c1f908166847040153620'
         '7e5b9031ef403a7cf3a143e9fa67263c'
         '96ab4517b48974ce0e566d9746a75a4f')
[ "$CARCH" = "i686" ] &&
md5sums=('26cecc80a896224a21f357c78c76db26'
         'ebc707d3348c1f908166847040153620'
         '7e5b9031ef403a7cf3a143e9fa67263c'
         '96ab4517b48974ce0e566d9746a75a4f')
install="mongodb.install"

package() {
    install -d "$pkgdir/usr/bin"
    install -D $srcdir/mongodb-linux-$CARCH-${pkgver}/bin/* $pkgdir/usr/bin 
    install -Dm755 $startdir/mongodb.rc $pkgdir/etc/rc.d/mongodb
    install -Dm644 $startdir/mongodb.conf $pkgdir/etc/mongodb.conf
    install -Dm644 $srcdir/mongodb.service $pkgdir/usr/lib/systemd/system/mongodb.service
    install -dm700 $pkgdir/var/lib/mongodb
    install -dm755 $pkgdir/var/log/mongodb

    if [ -d "$pkgdir/usr/lib64" ]
    then
        mv "$pkgdir/usr/lib64" "$pkgdir/usr/lib"
    fi
}
