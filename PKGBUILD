# vim:set ft=sh:
# Maintainer: BlackEagle < ike DOT devolder AT gmail DOT com >
pkgname=sysbench
_basever=1.0
pkgver=1.0.20171217.b9c6b3a
pkgrel=1
pkgdesc="Modular, cross-platform and multi-threaded benchmark tool for evaluating OS parameters that are important for a system running a database under intensive load."
url="https://github.com/akopytov/sysbench"
arch=('x86_64')
license=('GPL')
makedepends=('git')
depends=('libmariadbclient' 'xxd')
source=("$pkgname::git+https://github.com/akopytov/sysbench.git#branch=$_basever")
sha256sums=('SKIP')

pkgver() {
    cd "$pkgname"
    echo $_basever.$(git log -1 --format="%ci" | sed 's/.*\([0-9]\{4\}\)-\([0-9]\{2\}\)-\([0-9]\{2\}\).*/\1\2\3/').$(git rev-parse --short HEAD)
}

build() {
    cd "$pkgname"
    ./autogen.sh
    ./configure --prefix=/usr
    make
}

package() {
    cd "$pkgname"
    make DESTDIR="$pkgdir" install
}
