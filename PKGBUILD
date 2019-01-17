pkgname=plex-media-server
pkgver=1.14.1.5488
_pkgsum=cc260c476
pkgrel=1
pkgdesc='Plex Media Server'
arch=('x86_64')
url='https://plex.tv/'
license=('custom')
depends=('systemd')
backup=('etc/conf.d/plexmediaserver')
install='plex-media-server.install'
source=("https://downloads.plex.tv/${pkgname}/${pkgver}-${_pkgsum}/plexmediaserver-${pkgver}-${_pkgsum}.x86_64.rpm"
        'plexmediaserver.conf.d'
        'plexmediaserver.service'
        'plexmediaserver.sh'
        'terms.txt')
md5sums=('fafb64a6cc876478964e563af35ea1bd'
         'acf8e4ede01b20819eb1a529a64e923a'
         'c8e233369a15b6452599fee529a33c44'
         '6d328756dc99c3efc266cd59d2641979'
         '6c43875003b842ff4cd5b7e9886fed78')

package() {
    install -dm 755 ${pkgdir}/{opt,etc/conf.d,usr/{bin,lib/systemd/system}}
    cp -dr --no-preserve='ownership' usr/lib/plexmediaserver ${pkgdir}/opt/
    install -m 755 plexmediaserver.sh ${pkgdir}/usr/bin/
    install -m 644 plexmediaserver.service ${pkgdir}/usr/lib/systemd/system/
    install -m 644 plexmediaserver.conf.d ${pkgdir}/etc/conf.d/plexmediaserver

    install -dm 755 ${pkgdir}/var/lib/plex
    chown 421:421 -R ${pkgdir}/var/lib/plex

    install -dm 755 ${pkgdir}/usr/share/licenses/${pkgname}
    install -m 644 terms.txt ${pkgdir}/usr/share/licenses/${pkgname}/
}
