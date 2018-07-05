# Contributor: Oleksiy Zakharov <alexzkhr@gmail.com>
pkgname=VC4C
pkgver=0.4.0
pkgrel=2
pkgdesc="OpenCL implementation running on the VideoCore IV GPU of the Raspberry Pi models"

provides=('VC4CL')
arch=('arm' 'armv6h')
url="git://github.com/doe300/VC4CL"

license=('MIT')
depends=(VC4C opencl-headers ocl-icd)
makedepends=(cmake)
source=(git://github.com/doe300/VC4CL)
        
md5sums=('SKIP')


build() {  
  mkdir -p ${srcdir}/build
  cd ${srcdir}/build
  cmake -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_DEB_PACKAGE=OFF -DVC4C_HEADER_PATH=/usr/include/vc4cc/VC4C.h -DVC4CC_LIBRARY=/usr/lib/libVC4CC.so ../VC4CL
  make || return 1
}

package() {
  cd $srcdir/build
  make DESTDIR="$pkgdir/" install  
}
