# Maintainer; BlackEagle < ike DOT devolder AT gmail DOT com >
# Contributor: Valeriy Lyasotskiy <onestep@ukr.net>
# Contributor: Zom <zom@eevul.org>

pkgname=kpackagekit
pkgver=0.6.3.3
pkgrel=2
pkgdesc="KDE tools for PackageKit"
arch=('i686' 'x86_64')
url="http://www.kde-apps.org/content/show.php/KPackageKit?content=84745"
license=('GPL')
depends=('kdelibs' 'packagekit-qt>=0.6.11')
makedepends=('cmake' 'automoc4')
source=(
	"http://kde-apps.org/CONTENT/content-files/84745-${pkgname}-${pkgver}.tar.bz2"
	"kubuntu_08_ktoolinvocation.diff"
)
sha256sums=(
	'd1f969062f2dbbdcef2ea4f80a95c4072136b46c1e2e094d2500752b6857c300'
	'6eb00340476fcd9f817f8047b13b3653590071fd8dbc9874786e80991a9c08db'
)

build() {
	cd ${pkgname}-${pkgver}
	patch -Np1 -i ${srcdir}/kubuntu_08_ktoolinvocation.diff
	[ -d "build" ] && rm -rf build
	mkdir build
	cd build

	cmake ../ \
		-DCMAKE_BUILD_TYPE=Release \
		-DCMAKE_INSTALL_PREFIX=/usr
	make
}

package() {
	cd ${pkgname}-${pkgver}
	cd build
	make DESTDIR=${pkgdir} install
}
