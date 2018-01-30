# $Id$
# Maintainer: Marco Pompili
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Dag Odenhall <dag.odenhall@gmail.com>
# Contributor: Grigorios Bouzakis <grbzks@gmail.com>

pkgname=dwm-br1
pkgver=6.1
pkgrel=4
pkgdesc="A dynamic window manager for X"
url="http://dwm.suckless.org"
arch=('i686' 'x86_64')
license=('MIT')
options=(zipman)
depends=('libx11' 'libxinerama' 'libxft' 'freetype2' 'st-br1' 'dmenu')
conflicts=('dwm')
provides=('dwm')
install=dwm.install
source=('dwm-br1::git+https://github.com/marcopompili/dwm-br1.git'
	'config.h'
	'dwm.desktop')
sha256sums=('SKIP'
            'SKIP'
            'bc36426772e1471d6dd8c8aed91f288e16949e3463a9933fee6390ee0ccd3f81')

prepare() {
  cd ${srcdir}/${pkgname}  
  cp ${srcdir}/config.h config.h
}

build() {
  cd ${srcdir}/${pkgname}
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
}

package() {
  cd ${srcdir}/${pkgname}
  make PREFIX=/usr DESTDIR=${pkgdir} install
  install -m644 -D LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
  install -m644 -D README ${pkgdir}/usr/share/doc/${pkgname}/README
  install -m644 -D ${srcdir}/dwm.desktop ${pkgdir}/usr/share/xsessions/dwm.desktop
}
