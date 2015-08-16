
#Maintainer: Yichao Yu <yyc1992@gmail.com>
#Contributor: Yichao Yu <yyc1992@gmail.com>

pkgname=hybrid-im-git
pkgver=20120522
pkgrel=1
arch=('i686' 'x86_64')
license=('GPL')
makedepends=('git' 'cmake')
depends=('gtk2' 'gdk-pixbuf2' 'glib2' 'openssl' 'libxml2' 'libnotify' 'gstreamer0.10' 'libxss' 'networkmanager' 'dbus-glib' 'libwebkit')
url='https://github.com/levin108/hybrid'
pkgdesc="Hybird is an lightweight IM framework, currently supports China Mobile Fetion protocol and xmpp protocol."

_gitroot='https://github.com/levin108/hybrid.git'
_gitname='hybrid'
build() {
  cd "$srcdir"
  msg "Connecting to github.com"

  if [ -d "$_gitname" ] ;then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot"
  fi
  msg "GIT checkout done or server timeout"

  cd "$srcdir/$_gitname"

  git checkout master
  mkdir -p build
  cd build
  cmake .. -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd "$srcdir/$_gitname/build"
  make DESTDIR="${pkgdir}" install
}
