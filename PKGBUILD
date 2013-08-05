# Contributor: Alexandre Défossez <alexandre.defossez at google famous mailing service>
pkgname=pydoctor
pkgver=0.4
pkgrel=1
pkgdesc="An epydoc-like tool"
arch=('any') # python
url="http://codespeak.net/~mwh/pydoctor/"
license=('custom')
depends=('python2' 'nevow' 'twisted' 'zope-interface')
source=(
"https://pypi.python.org/packages/source/p/pydoctor/pydoctor-$pkgver.tar.gz"{,.asc}
)
md5sums=(b7564e12b5d35d4cb529a2c220b25d3a SKIP)

build() {
  cd "$srcdir/pydoctor-$pkgver"
  python2 setup.py build
} 

package(){
  cd "$srcdir/pydoctor-$pkgver"
  python2 setup.py install --root="$pkgdir"
  install -D -m644 LICENSE.txt $pkgdir/usr/share/licenses/$pkgname/LICENSE
}
