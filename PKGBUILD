pkgname=plex-media-server
pkgver=0.9.11.4.739
_pkgsum=a4e710f
pkgrel=1
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
        
sha256sums=('a82829854ab8e780f7686a9e65d36c8cf6900d6c3471176e0f2aae8f5a024a19'
            'ea50f866c7aa6b0a9e71d830887fb081b70f34f0b4b36f7cd7a69ab48b81d371'
            'b55368f164da76696215153a7a2d880097f1e3ccdba9faf5a3690706407eb7bb'
            '7bb97271eb2dc5d1dcb95f9763f505970d234df17f1b8d79b467b9020257915a'
            '6466e67868a7e0422143811937cbf2abb96fa2698b1d73ace58b519cc78d8288')

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

# vim: ts=2 sw=2 et:
