# $Id$
# Maintainer: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: tobias <tobias funnychar archlinux.org>
# Adjusted by Ivan K <ivan@sq10.net>

pkgname=xfwm4
pkgver=4.12.3
pkgrel=2
pkgdesc="Xfce window manager"
arch=('i686' 'x86_64')
url="http://www.xfce.org/"
license=('GPL2')
groups=('xfce4')
depends=('libxfce4ui' 'libwnck' 'libdrm' 'hicolor-icon-theme')
makedepends=('intltool')
source=(http://archive.xfce.org/src/xfce/$pkgname/${pkgver%.*}/$pkgname-$pkgver.tar.bz2)
sha256sums=('f4a988fbc4e0df7e8583c781d271559e56fd28696092f94ae052e9e6edb09eac')

prepare() {
  cd "$srcdir/$pkgname-$pkgver"

  patch src/events.c ../../remove_title_bar_middle_click_functionality.patch
}

build() {
  cd "$srcdir/$pkgname-$pkgver"

  ./configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --libexecdir=/usr/lib \
    --localstatedir=/var \
    --disable-static \
    --enable-startup-notification \
    --enable-randr \
    --enable-compositor \
    --enable-xsync \
    --disable-debug
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
}

# vim:set ts=2 sw=2 et:
