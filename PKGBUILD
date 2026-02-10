# Maintainer: James P. Harvey <jamespharvey20 at gmail dot com>

pkgname=boost-di
_pkgname=di
pkgver=1.3.2
pkgrel=1
pkgdesc="Boost (experimental) c++14 dependency injection library"
arch=('any')
url="https://github.com/boost-ext/${_pkgname}"
license=('Boost')
makedepends=('cmake')
source=("${pkgname}.tar.gz::https://github.com/boost-ext/${_pkgname}/archive/v${pkgver}.tar.gz")
sha256sums=('2bcd01f1d555bdb59a277b932f9021701c5cd26d1d7411f024394db69c5c11cf')

build() {
   cd "${srcdir}/${_pkgname}-${pkgver}"
   mkdir build && cd build
   cmake -DCMAKE_CXX_STANDARD=14 -DBOOST_DI_OPT_BUILD_TESTS=OFF ..
   make
}

check() {
   cd "${srcdir}/${_pkgname}-${pkgver}/build"
   # let user know this test isn't hung, because it will take around a minute even though tons of prior tests were nearly instant
   echo "*** test.ft_di_errors will take at least a minute ***"
   ctest
}

package() {
   cd "${srcdir}/${_pkgname}-${pkgver}/include/boost"
   install -Dm644 di.hpp "${pkgdir}/usr/include/${pkgname}/di.hpp"
   cp -r di "${pkgdir}/usr/include/${pkgname}"
}
