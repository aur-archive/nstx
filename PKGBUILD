pkgname=nstx
pkgver=1.1.beta6
_pkgver=1.1-beta6
pkgrel=5
pkgdesc="IP over DNS tunnel"
arch=('i686' 'x86_64')
url="http://dereference.de/nstx/"
license=('GPL2')
depends=('kernel-headers')
makedepends=('patch')
source=(http://ftp.de.debian.org/debian/pool/main/n/${pkgname}/${pkgname}_${_pkgver}.orig.tar.gz
	http://ftp.de.debian.org/debian/pool/main/n/${pkgname}/${pkgname}_${_pkgver}-${pkgrel}.diff.gz)

md5sums=('275abd75a856b07a798b1f2360088cf5'
         '0b7b4d4d3added258ff61b1c5357a1b9')

build() {
  cd "${srcdir}/${pkgname}-${_pkgver}"

  patch -Np1 -i "${srcdir}/${pkgname}_${_pkgver}-${pkgrel}.diff" || return 1

  make || return 1
  mkdir -p ${pkgdir}/usr/sbin/
  install -m 755 nstxd nstxcd ${pkgdir}/usr/sbin/
  mkdir -p ${pkgdir}/usr/share/man/man8
  for man in *.8 ; do
    install -m644 ${man} ${pkgdir}/usr/share/man/man8/
  done
  mkdir -p ${pkgdir}/usr/share/doc/nstx
  for doc in README Changelog ; do
      install -m644 ${doc} ${pkgdir}/usr/share/doc/nstx
  done
}
