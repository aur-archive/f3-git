# Maintainer:   Lucky <archlinux@builds.lucky.li>

pkgname=f3-git
_pkgname="${pkgname%-*}"
pkgver=5.0.r12.g902db29
pkgrel=2
pkgdesc="Integrity test for data media, especially for recognising USB sticks and SD cards that have been tampered with. An alternative to h2testw"
url="http://oss.digirati.com.br/f3/"
license=("GPL3")
arch=("i686" "x86_64")
depends=("parted")
install=${pkgname}.install
source=("git://github.com/AltraMayor/${_pkgname}.git")
md5sums=("SKIP")

pkgver() {
  cd "${_pkgname}"
  git describe --long --tags | sed -r 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd "${srcdir}/${_pkgname}"
  make all experimental
}

package() {
  cd "${srcdir}/${_pkgname}"

  #all
  install -Dm755 "f3write"      "${pkgdir}/usr/bin/f3write"
  install -Dm755 "f3read"       "${pkgdir}/usr/bin/f3read"

  install -Dm755 "f3write.h2w"  "${pkgdir}/usr/bin/f3write.h2w"
  install -Dm755 "log-f3wr"     "${pkgdir}/usr/bin/log-f3wr"

  #experimental
  install -Dm755 "f3fix"    "${pkgdir}/usr/bin/f3fix"
  install -Dm755 "f3probe"  "${pkgdir}/usr/bin/f3probe"

  # disabled » https://github.com/AltraMayor/f3/issues/7#issuecomment-68633090
  #install -Dm755 "f3brew"   "${pkgdir}/usr/bin/f3brew"

  install -Dm644 "LICENSE"  "${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE"
  install -Dm644 "f3read.1" "${pkgdir}/usr/share/man/man1/f3read.1"
}
