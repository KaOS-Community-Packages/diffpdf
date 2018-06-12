pkgname=diffpdf
pkgver=2.1.3.1
pkgrel=1
pkgdesc="Diffing pdf files visually or textually"
url="https://gitlab.com/eang/diffpdf"
screenshot="http://www.qtrac.eu/diffpdf.png"
license=('GPL2')
arch=('x86_64')
depends=('poppler' 'hicolor-icon-theme' 'curl' 'nspr')
makedepends=('cmake' 'extra-cmake-modules' 'qt5-tools')
source=("https://gitlab.com/eang/diffpdf/-/archive/v${pkgver}/${pkgname}-v${pkgver}.tar.gz"
        "diffpdf.desktop")
md5sums=('e838cda78d763495e0c0671f704c7059'
         'f3b3ea2aae0066d6b36e54793f248213')

build() {
  cd ${srcdir}/${pkgname}-v${pkgver}/
  msg "### cmake"
  cmake -D CMAKE_INSTALL_PREFIX="/usr" .
  msg "### make"
  make
}

package() {
  cd ${srcdir}/${pkgname}-v${pkgver}/
  msg "### make install"
  make DESTDIR=${pkgdir} install

  _appdir=${pkgdir}/usr/share/applications
  _licdir=${pkgdir}/usr/share/licenses/${pkgname}
  _tradir=${pkgdir}/usr/share/${pkgname}/translations
  install -dpm755 ${_licdir} ${_tradir}
  rm -v ${_appdir}/*
  install -Dpm644 ${srcdir}/diffpdf.desktop ${_appdir}/
  install -Dpm644 gpl-2.0.txt ${_licdir}/
  install -Dpm644 *.qm ${_tradir}/
}
