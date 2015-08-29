pkgname=plex-media-server
pkgver=0.9.12.11.1406
_pkgsum=8403350
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
sha256sums=('295174b3617d699f11ecc22bc603a579e2291fe6ba55a536711acafd64455390'
            'a82829854ab8e780f7686a9e65d36c8cf6900d6c3471176e0f2aae8f5a024a19'
            'ea50f866c7aa6b0a9e71d830887fb081b70f34f0b4b36f7cd7a69ab48b81d371'
            '7e5e5e667739bd35f16b7de5edd5846b0ed555a0f61a17aa65e5d623e878f25d'
            '7bb97271eb2dc5d1dcb95f9763f505970d234df17f1b8d79b467b9020257915a')

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
