pkgname=plex-media-server
pkgver=1.5.5.3634
_pkgsum=995f1dead
pkgrel=1
pkgdesc='Plex Media Server'
arch=('x86_64')
url='https://plex.tv/'
license=('custom: https://www.plex.tv/about/privacy-legal/plex-terms-of-service/')
backup=('etc/conf.d/plexmediaserver')
install='plex-media-server.install'
source=("https://downloads.plex.tv/plex-media-server/${pkgver}-${_pkgsum}/plexmediaserver-${pkgver}-${_pkgsum}.x86_64.rpm"
        'plexmediaserver.conf.d'
        'plexmediaserver.service'
        'plex.conf'
        'terms.txt')
md5sums=('47d2026555372b7fa0508ce615e512a6'
         'ce68337bf5cdfb8b2183cc1180382d11'
         '4fa33957d99a87260dca9b309cd9e5d4'
         '146e68120138449e9e9d1483fb0624c8'
         '6c43875003b842ff4cd5b7e9886fed78')
         
package() {
    install -dm 755 ${pkgdir}/{opt,etc/conf.d,usr/{bin,lib/systemd/system}}
    cp -dr --no-preserve='ownership' usr/lib/plexmediaserver ${pkgdir}/opt/
    install -m 644 plexmediaserver.service ${pkgdir}/usr/lib/systemd/system/
    install -m 644 plexmediaserver.conf.d ${pkgdir}/etc/conf.d/plexmediaserver

    install -Dm 644 ${srcdir}/plex.conf ${pkgdir}/usr/lib/sysusers.d/plex.conf

    install -dm 755 ${pkgdir}/usr/share/licenses/plex-media-server
    install -m 644 terms.txt ${pkgdir}/usr/share/licenses/plex-media-server/
}

# vim: ts=2 sw=2 et:
