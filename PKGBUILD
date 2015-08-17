# Contributor: john_schaf

pkgname=pastix
pkgver=5.2.2
pkgrel=2
pkgdesc="high performance parallel solver for very large sparse linear systems based on direct methods."
arch=('x86_64')
url="http://pastix.gforge.inria.fr/"
license=('CeCILL-C')
depends=('scotch' 'hwloc')
replaces=()
conflicts=()
provides=()
options=('staticlibs')
source=(https://gforge.inria.fr/frs/download.php/33274/pastix_release_bugfix3_6eafa91.tar.bz2 config.in)
md5sums=('eaa6ec23b93d7392f730a022ccf747c9' 'c8068872daf63b590699405f2ee44dc9')

extractdir=pastix_release_6eafa91

build() {
  cd "${srcdir}/${extractdir}/src"
  cp "${srcdir}/config.in" .
  echo "cat ./Revision" > myversion.sh
  make all
  make install
}

package() {
  cd "${srcdir}/${extractdir}/install"
  sed 's/="-.*install/="/' pastix-conf > bin/pastix-conf
  install -D -m 644 include/pastix.h "$pkgdir/usr/include/pastix.h"
  install -D -m 644 include/* "$pkgdir/usr/include/"
  install -D -m 644 lib/libpastix.a "$pkgdir/usr/lib/libpastix.a"
  install -D -m 644 lib/* "$pkgdir/usr/lib/"
  install -D -m 755 bin/pastix-conf "$pkgdir/usr/bin/pastix-conf"
}

# vim:set ts=2 sw=2 et:
