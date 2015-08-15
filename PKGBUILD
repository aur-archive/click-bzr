pkgname=click-bzr
_pkgname=click
pkgver=65
pkgrel=1
pkgdesc='Provisional simplified packaging format that installs in a separate part of the file system, suitable for third-party applications'
arch=('i686' 'x86_64')
url='https://launchpad.net/click'
license=('GPL3')
depends=('python-apt' 'python-debian')
makedepends=('bzr')
source=(bzr+lp:ubuntu/$_pkgname)
md5sums=('SKIP')

pkgver() {
  cd $_pkgname
  bzr revno
}

build() {
  cd $srcdir/$_pkgname
  export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/lib/pkgconfig
  ./autogen.sh
  ./configure --prefix=/usr \
              --sysconfdir=/etc \
              --with-systemdsystemunitdir=/usr/lib/systemd/system \
              --with-systemduserunitdir=/usr/lib/systemd/user \
              --disable-packagekit
  make
}

package() {
  cd $srcdir/$_pkgname
  make install DESTDIR=$pkgdir PYTHON_INSTALL_FLAGS=--root=$pkgdir
}
