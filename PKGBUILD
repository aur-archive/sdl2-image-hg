pkgname=sdl2-image-hg
pkgver=380
pkgrel=1
pkgdesc="hg build of sdl2_image"
arch=('i686' 'x86_64')
url="http://www.libsdl.org"
license=('MIT')
depends=(sdl2-hg)
makedepends=(mercurial)
optdepends=(libpng libtiff libjpeg libwebp)
provides=(sdl2_image)
conflicts=(sdl2_image)
options=(!libtool)
source=('sdl2_image::hg+http://hg.libsdl.org/SDL_image')
md5sums=('SKIP')

_hgrepo="sdl2_image"

pkgver() {
  cd "${srcdir}/${_hgrepo}"
  hg identify -n
}

prepare() {
  mkdir "${srcdir}/${_hgrepo}/build"
}

build() {
  cd "${srcdir}/${_hgrepo}/"
  ./autogen.sh
  cd "${srcdir}/${_hgrepo}/build"
  ../configure --disable-static --prefix=/usr
  make
}

package() {
  cd "${srcdir}/${_hgrepo}/build"
  make DESTDIR="${pkgdir}/" install
  install -Dm644 ../COPYING.txt "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
## vim:set ts=2 sw=2 et:
