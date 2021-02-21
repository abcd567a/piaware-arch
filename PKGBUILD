#Contributor: abcd567
#Maintainer: abcd567

pkgname=piaware
pkgver=latest
pkgrel=1

pkgdesc="Flightaware ADS-B data feeder"

arch=('i686' 'i386' 'x86_64' 'armv6h' 'armv7h' 'armv8h' 'aarch64')
url="https://github.com/flightaware/piaware"
license=('BSD')

depends=('git' 'autoconf' 'tcl' 'tcllib' 'tclx' 'tcltls'
         'python' 'tk' 'tcllauncher' 'net-tools')

source=('piaware::git+git://github.com/flightaware/piaware'
        'faup1090::git+git://github.com/flightaware/dump1090'
        'fa-mlat-client::git://github.com/mutability/mlat-client.git')

md5sums=('SKIP' 'SKIP' 'SKIP')

install=piaware.install

pkgver() {
  cd ${srcdir}/piaware
  git describe --tags | sed 's/-.*//'
}

package() {
## Build faup1090
  cd ${srcdir}/faup1090
  make faup1090
  install -Dm755 ${srcdir}/faup1090/faup1090 ${pkgdir}/usr/lib/piaware/helpers/faup1090

## Build fa-mlat-client
  cd ${srcdir}/fa-mlat-client
  ./setup.py install --prefix=${pkgdir}/usr
  install -Dm755 ${pkgdir}/usr/bin/fa-mlat-client  ${pkgdir}/usr/lib/piaware/helpers/fa-mlat-client
  rm -rf ${pkgdir}/usr/bin/

## Build piaware
  cd ${srcdir}/piaware
  make install DESTDIR=${pkgdir} SYSTEMD=/usr/lib/systemd/system

  install -dm755 ${pkgdir}/var/cache/piaware
  install -dm750 ${pkgdir}/etc/sudoers.d/
  install -Dm644 etc/piaware.sudoers ${pkgdir}/etc/sudoers.d/01piaware
  install -Dm640 ../../piaware.conf ${pkgdir}/etc/piaware.conf
  chmod -x ${pkgdir}/usr/lib/systemd/system/piaware.service
  install -Dm644 LICENSE.txt ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
}
