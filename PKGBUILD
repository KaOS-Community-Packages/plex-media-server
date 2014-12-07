pkgname=plex-media-server
pkgver=0.9.11.4.739
_pkgsum=a4e710f
pkgrel=2
pkgdesc='Plex Media Server'
arch=('x86_64')
url='https://plex.tv/'
license=('custom')
depends=('systemd')
backup=('etc/conf.d/plexmediaserver')
install='plex-media-server.install'
source=("https://downloads.plex.tv/plex-media-server/${pkgver}-${_pkgsum}/plexmediaserver-${pkgver}-${_pkgsum}.x86_64.rpm"
        'plexmediaserver.conf.d'
        'plexmediaserver.service'
        'plexmediaserver.sh'
        'terms.txt')
        
md5sums=('c5876e81200bd0b70ae74beee8b2a141'
         'acf8e4ede01b20819eb1a529a64e923a'
         'c8e233369a15b6452599fee529a33c44'
         '21ba695c7568e117850f9dd63d14b418'
         'bd703bc750b989a27edd590eb8c8e9d7')

package() {
  install -dm 755 "${pkgdir}"/{opt,etc/conf.d,usr/{bin,lib/systemd/system}}
  cp -dr --no-preserve='ownership' usr/lib/plexmediaserver "${pkgdir}"/opt/
  install -m 755 plexmediaserver.sh "${pkgdir}"/usr/bin/
  install -m 644 plexmediaserver.service "${pkgdir}"/usr/lib/systemd/system/
  install -m 644 plexmediaserver.conf.d "${pkgdir}"/etc/conf.d/plexmediaserver

  install -dm 755 "${pkgdir}"/var/lib/plex
  chown 421:421 -R "${pkgdir}"/var/lib/plex

  install -dm 755 "${pkgdir}"/usr/share/licenses/plex-media-server
  install -m 644 terms.txt "${pkgdir}"/usr/share/licenses/plex-media-server/
}

