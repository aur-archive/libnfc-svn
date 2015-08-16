# Maintainer: Pascal E. <archlinux at hardfalcon dot net>
# Contributor: Andrej Gelenberg <andrej.gelenberg at udo dot edu>
pkgname=libnfc-svn
pkgver=1469
pkgrel=1
pkgdesc="libnfc is the first free NFC SDK and Programmers API"
arch=('i686' 'x86_64')
url=("http://www.libnfc.org/documentation/introduction" "https://code.google.com/p/libnfc/")
license=('LGPL3')

depends=('pcsclite' 'libusb')
makedepends=('doxygen' 'zip' 'svn')
provides=(libnfc)
conflicts=(libnfc)

_svntrunk=https://libnfc.googlecode.com/svn/trunk/
_svnmod=libnfc

build()
{
  cd ${srcdir}

  if [ -d $_svnmod/.svn ]
  then
    cd ${_svnmod}
    svn up -r ${pkgver}
  else
    svn co ${_svntrunk} --config-dir ./ -r ${pkgver} ${_svnmod}
  fi

  cd ${srcdir}/${_svnmod}
  ./make_release.sh
  
  ./configure --prefix /usr
   make
   make DESTDIR=$pkgdir install
}
