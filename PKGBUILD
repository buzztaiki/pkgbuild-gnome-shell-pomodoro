# Maintainer:  Marcin Wieczorek <marcin@marcin.co>
# Contributor: Andrejs Mivreņiks <gim at fastmail dot fm>
# Contributor: Janne Haapsaari <haaja@iki.fi>
# Contributor: maus25 <mirko378@gmail.com>

pkgname=gnome-shell-pomodoro
pkgver=0.15.1
pkgrel=1
pkgdesc='A time management utility for GNOME based on the pomodoro technique'
arch=('i686' 'x86_64')
url='https://github.com/codito/gnome-pomodoro'
license=('GPL3')
depends=('gnome-desktop' 'gstreamer' 'gobject-introspection' 'libpeas' 'appstream-glib' 'gom')
makedepends=('intltool' 'vala' 'gnome-common' 'docbook2x' 'perl-xml-sax-expat')
changelog='NEWS'
source=("$pkgname-$pkgver.tar.gz::https://github.com/codito/gnome-pomodoro/archive/$pkgver.tar.gz"
        "pr395.patch::https://github.com/codito/gnome-pomodoro/commit/0c249f36b66e85ee5132cabb23aad4747fc5545d.patch"
        "pr396.patch::https://github.com/codito/gnome-pomodoro/commit/23b0e344fe939a41d6ecc874b49403fa4e03566d.patch"
	"resize.patch::https://github.com/codito/gnome-pomodoro/commit/92a285134c05e671648aa4335c81b182132f22e9.patch")
sha256sums=('67c90673ba6362fb1dea2cc72aa5a2e6a8b75f0141388cf5a48e31d078ecffb3'
            '7ab9a0f289b1f2ae25cc206fee2003c25a3d29b452ddd9a721c4c9546a4fad83'
            '56616288bd63c58dce79a035988f7013f2f36330063c345326794de1dc274a82'
            'd8cd9c4db16e37642f0264855e0031bed635b8c6056eefe6f8b13616e6c03f13')

prepare() {
  cd "$srcdir/gnome-pomodoro-$pkgver"
  ./autogen.sh --prefix=/usr --datadir=/usr/share
  patch -Np1 -i ../pr395.patch
  patch -Np1 -i ../pr396.patch
  patch -Np1 -i ../resize.patch
}

build() {
  cd "$srcdir/gnome-pomodoro-$pkgver"
  make
}

package() {
  cd "$srcdir/gnome-pomodoro-$pkgver"
  make DESTDIR="$pkgdir" install
}
