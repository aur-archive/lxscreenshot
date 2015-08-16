pkgname=lxscreenshot
pkgver=23
pkgrel=1
pkgdesc="a screenshot tool for the LXDE project"
arch=('i686' 'x86_64')
url='http://launchpad.net/~lubuntu-software-center-team'
license=('GPL3')
depends=('gobject-introspection' 'gtk3')
makedepends=('bzr' 'intltool' 'vala')
_bzrmod='lxscreenshot'
_bzrtrunk=lp:lxscreenshot
md5sums=()

build() {
  cd "$srcdir"
  if [ -d ${_bzrmod} ] ; then
    bzr up ${_bzrmod} -r ${pkgver}
    msg "The local files are updated."
  else
    bzr co ${_bzrtrunk} ${_bzrmod} -r ${pkgver}
  fi

  cd "$pkgname"
  ./autogen.sh
  ./configure --prefix=/usr
  make
}

package() {
  cd "${srcdir}/$pkgname"
  make prefix="$pkgdir"/usr install
}