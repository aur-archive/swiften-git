pkgname=swiften-git
pkgver=20130304
pkgrel=1
pkgdesc="XMPP Client Library"
arch=('i686' 'x86_64')
url="http://swift.im/"
license=('GPL3')
groups=()
depends=('libidn' 'avahi' 'libxss' 'expat' 'openssl' 'boost-libs' 'libxml2' 'libidn' 'qt4')
makedepends=('git' 'scons' 'boost')
provides=('swiften')
conflicts=('swiften')
replaces=()
backup=()
options=()
noextract=()

_gitroot="git://swift.im/swift"
_gitname="swift"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  scons V=1 swiften_dll=1 Swiften SWIFTEN_INSTALLDIR=${pkgdir}/usr ${pkgdir}/usr

} 
# vim:set ts=2 sw=2 et:


