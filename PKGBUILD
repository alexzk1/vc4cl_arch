# Contributor: Oleksiy Zakharov <alexzkhr@gmail.com>
pkgname=VC4CL
pkgver=0.4.0
pkgrel=3
pkgdesc="OpenCL implementation running on the VideoCore IV GPU of the Raspberry Pi models"

provides=('VC4CL')
arch=('arm' 'armv6h' 'armv7h' 'aarch64')
url="git://github.com/doe300/VC4CL"

license=('MIT')
depends=(VC4C opencl-headers ocl-icd )
makedepends=(cmake)
source=(git://github.com/doe300/VC4CL)
        
md5sums=('SKIP')


build() {    
  cd ${srcdir}/VC4CL
  #backend has 2 ways to access GPU, through /dev/mem (DREGISTER_POKE_KERNELS=ON) and
  #using ioctl codes ("mailbox") - DREGISTER_POKE_KERNELS=OFF
  cmake -DREGISTER_POKE_KERNELS=ON -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_DEB_PACKAGE=OFF -DVC4C_HEADER_PATH=/usr/include/vc4cc/VC4C.h -DVC4CC_LIBRARY=/usr/lib/libVC4CC.so
  make || return 1
}

package() {
  cd $srcdir/VC4CL
  make DESTDIR="$pkgdir/" install  
}
