# Merged with official ABS kjsembed PKGBUILD by dr460nf1r3, 2021/12/05 (all respective contributors apply herein)
# Contributor: Antonio Rojas <arojas@archlinux.org>

pkgname=plasma-thunderbolt-git
pkgver=5.22.90_r156.g579cef8
pkgrel=1
pkgdesc='Plasma integration for controlling Thunderbolt devices'
arch=(x86_64)
url='https://kde.org/plasma-desktop/'
license=(LGPL)
depends=(bolt systemsettings-git)
makedepends=(cmake git extra-cmake-modules-git)
groups=(plasma-git)
source=("git+https://invent.kde.org/plasma/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(git describe | sed 's/^v//;s/-.*//')"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
