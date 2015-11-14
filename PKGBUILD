# $Id$
# Maintainer: Dimitar Pashov <d.pashov@gmail.com>
## mostly copied from the official ArchLinux package PKGBUILD

pkgname=pssh-dmt4
pkgver=2.3.1p
pkgrel=0
pkgdesc="Parallel versions of the openssh tools ssh, scp, rsync, nuke, slurp"
arch=('any')
url="https://github.com/dmt4/pssh"
license=('BSD')
depends=('openssh' 'python')
makedepends=('git')
source=("$pkgname"::'git+https://github.com/dmt4/pssh.git')
sha256sums=('SKIP')

package() {
  cd "${srcdir}"/$pkgname
  python setup.py install --root "${pkgdir}"

# fix manpages
  install -d "${pkgdir}"/usr/share
  mv "${pkgdir}"/usr/man  "${pkgdir}"/usr/share

# fix putty pscp file conflict
  mv "${pkgdir}"/usr/bin/pscp  "${pkgdir}"/usr/bin/psshscp
  mv "${pkgdir}"/usr/share/man/man1/pscp.1  "${pkgdir}"/usr/share/man/man1/psshscp.1

# license
  install -Dm644 COPYING "${pkgdir}"/usr/share/licenses/$pkgname/COPYING
}