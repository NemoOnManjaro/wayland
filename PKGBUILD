# Maintainer: Sébastien Luttringer <seblu@archlinux.org>
# Contributor: Tom Gundersen <teg@jklm.no>
# Contributor: Joel Teichroeb <joel@teichroeb.net>

pkgbase=wayland
pkgname=(wayland)
pkgver=1.24.0
pkgrel=1
pkgdesc='A computer display server protocol'
arch=('x86_64')
url='https://wayland.freedesktop.org/'
license=('MIT')
depends=('glibc' 'libffi' 'expat' 'libxml2' 'default-cursors')
makedepends=('meson' 'libxslt' 'doxygen' 'xmlto' 'graphviz' 'docbook-xsl')
source=("https://gitlab.freedesktop.org/wayland/wayland/-/releases/$pkgver/downloads/wayland-$pkgver.tar.xz")
sha256sums=('82892487a01ad67b334eca83b54317a7c86a03a89cfadacfef5211f11a5d0536')

build() {
  arch-meson $pkgbase-$pkgver build -Ddocumentation=false
  meson compile -C build
}

check() {
  meson test -C build --print-errorlogs
}

package_wayland() {
  provides=(libwayland-{client,cursor,egl,server}.so)

  meson install -C build --destdir "$pkgdir"
}

# vim:set sw=2 sts=-1 et:
