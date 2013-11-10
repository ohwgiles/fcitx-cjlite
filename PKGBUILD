pkgname=fcitx-cjlite
pkgver=0.1
pkgrel=1
pkgdesc="Stripped custom Cangjie 5 table"
arch=('i686' 'x86_64')
url="https://github.com/ohwgiles/fcitx-cjlite/"
license=('GPL')
depends=('fcitx>=4.2.0')
makedepends=('cmake' 'intltool')
source=("git+https://github.com/ohwgiles/fcitx-cjlite/")
md5sums=('SKIP')

build() {
	cd "$builddir"
    cmake "$srcdir/$pkgname" -DCMAKE_INSTALL_PREFIX=/usr
    make
}

package() {
    cd "$builddir"
    make DESTDIR=$pkgdir install
}
