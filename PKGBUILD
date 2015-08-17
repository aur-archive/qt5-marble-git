# $Id: PKGBUILD 119239 2014-09-19 16:09:05Z bisson $
# Maintainer: Gaetan Bisson <bisson@archlinux.org>

pkgname=qt5-marble-git
_pkgname=marble
pkgver=20150205.6706316
pkgrel=1
pkgdesc='Virtual globe and world atlas'
url='https://marble.kde.org/'
license=('LGPL2.1')
arch=('i686' 'x86_64')
depends=('qt5-'{script,svg,tools,webkit})
makedepends=('git' 'cmake')
source=('git://anongit.kde.org/marble')
sha1sums=('SKIP')

provides=("${_pkgname}" 'kdeedu-marble')
conflicts=("${_pkgname}" 'kdeedu-marble')

pkgver() {
	cd "${srcdir}/${_pkgname}"
	git log -1 --format='%cd.%h' --date=short | tr -d -
}

build() {
	cd "${srcdir}/${_pkgname}"

	cmake \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DCMAKE_BUILD_TYPE=Release \
		-DQT5BUILD=1 \
		-DQTONLY=1 \
		.

	make
}

package() {
	cd "${srcdir}/${_pkgname}"
	make DESTDIR="${pkgdir}" install
}
