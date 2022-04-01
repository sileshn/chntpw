# Maintainer: Lukas Fleischer <lfleischer@archlinux.org>
# Contributor: Tobias Powalowski <tpowa@archlinux.org>

pkgname=chntpw
pkgver=140201
pkgrel=4
pkgdesc='Offline NT Password Editor - reset passwords in a Windows NT SAM user database file'
arch=('x86_64' 'aarch64')
url='http://pogostick.net/~pnh/ntpasswd/'
license=('GPL' 'LGPL')
makedepends=('openssl')
source=("http://pogostick.net/~pnh/ntpasswd/${pkgname}-source-${pkgver}.zip")
md5sums=('d60bc657206b07ad84d926649d6417dc')

prepare() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  sed -i 's/^CFLAGS= \(.*\) -m32 $/CFLAGS= \1/' Makefile
}

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  # install binaries, don't install static binaries!
  install -Dm0755 "${srcdir}/${pkgname}-${pkgver}/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
  install -Dm0755 "${srcdir}/${pkgname}-${pkgver}/reged" "${pkgdir}/usr/bin/reged"
  install -Dm0755 "${srcdir}/${pkgname}-${pkgver}/cpnt" "${pkgdir}/usr/bin/cpnt"

  for _f in *.txt; do
    install -Dm0644 "${_f}" "${pkgdir}/usr/share/doc/${pkgname}/${_f}"
  done
}
