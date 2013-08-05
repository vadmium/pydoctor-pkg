# Contributor: Alexandre Défossez <alexandre.defossez at google famous mailing service>
pkgname=pydoctor-bzr
pkgver=568
pkgrel=1
pkgdesc="An epydoc-like tool"
arch=('any') # python
url="http://codespeak.net/~mwh/pydoctor/"
license=('custom')
depends=('python2' 'nevow' 'twisted' 'zope-interface')
makedepends=('bzr')
provides=(pydoctor) 
conflicts=(pydoctor)

_bzrtrunk="lp:pydoctor"
_bzrmod="pydoctor"

build() {
  cd "$srcdir"
  msg "Connecting to Launchpad server...."

  if [ -d $_bzrmod ] ; then
    cd $_bzrmod
    bzr merge || return 1
    msg "The local files are updated."
  else
    bzr branch "$_bzrtrunk" || return 1
  fi

  msg "Bazaar checkout done or server timeout"

  rm -rf "$srcdir/$_bzrmod-build"
  cp -r "$srcdir/$_bzrmod" "$srcdir/$_bzrmod-build"
  cd "$srcdir/$_bzrmod-build"

  python2 setup.py build
} 

package(){
  cd "$srcdir/$_bzrmod-build"
  python2 setup.py install --root="$pkgdir"
  install -D -m644 LICENSE.txt $pkgdir/usr/share/licenses/$pkgname/LICENSE
}
