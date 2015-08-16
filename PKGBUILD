#maintainer: Gustavo Alvarez <sl1pkn07@gmail.com>

pkgname=kcalc-frameworks-git
pkgver=r1141.d72c067
pkgrel=2
pkgdesc="Scientific Calculator. KF5 Frameworks branch. (GIT version)"
url="https://www.kde.org/applications/utilities/kcalc"
arch=('x86_64')
license=('GPL' 'LGPL' 'FDL')
depends=('kxmlgui' 'knotifications')
makedepends=('extra-cmake-modules' 'kdoctools' 'git')
conflicts=('kdeutils-kcalc' 'kcalc')
provides=('kcalc')
source=("git://anongit.kde.org/kcalc.git#branch=frameworks")
sha1sums=('SKIP')
install="kcalc-frameworks-git.install"
_gitname=kcalc

pkgver() {
  cd "${_gitname}"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  rm -fr build
  mkdir -p build
}

build() {
  cd build

  cmake "../${_gitname}" \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
  make
}

package() {
  make -C build DESTDIR="${pkgdir}" install
}
