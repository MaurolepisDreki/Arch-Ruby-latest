# An up-to-date version of the Ruby interpreter
#
# Maintainer: Nile Aagard <inventerna@gmail.com>
pkgname=ruby
_pkgver="4.0"
pkgver="$_pkgver.6"
pkgrel=2
arch=('x86_64')
pkgdesc="Full Ruby $pkgver installation"
url="https://www.ruby-lang.org/en/"
license=('Ruby')
depends=('openssl' 'libyaml' 'zlib')
makedepends=('gcc' 'make')
optdepends=('libffi' 'gmp')
provides=('gem' 'rake' 'irb' 'rdbg' 'bundle' 'bundler' 'racc' 'rdoc' 'rbs' 'minitest' 'erb'
	# makepkg expands this to the soname, e.g. libruby.so=4.0-64
	'libruby.so'
	'rubygems=4.0.16' 'ruby-rubygems=4.0.16'
	'ruby-bundler=4.0.16' 'ruby-erb=6.0.1.1' 'ruby-irb=1.16.0'
	'ruby-minitest=6.0.0' 'ruby-racc=1.8.1' 'ruby-rake=13.3.1'
	'ruby-rbs=3.10.0' 'ruby-rdoc=7.0.4')
conflicts=('rubygems' 'ruby-rdoc' 'ruby-rbs' 'ruby-rake' 'ruby-racc' 'ruby-minitest' 'ruby-irb' 'ruby-erb' 'ruby-bundler')
backup=('etc/gemrc')
source=("https://cache.ruby-lang.org/pub/$pkgname/$_pkgver/$pkgname-$pkgver.tar.gz")
sha256sums=('837d299e8f7ddf2be31a229a7a7e019d354979825117989acb3b32b1a9be262a')

build() {
	cd "$pkgname-$pkgver"
	# LTO compiles code at link time; without -fPIC there, GCC picks
	# local-exec TLS for ruby_current_ec, which can't go in a shared object.
	# configure bakes this into the Makefile, so make needn't be given it.
	LDFLAGS="$LDFLAGS -fPIC" ./configure \
		--prefix=/usr \
		--sysconfdir=/etc \
		--localstatedir=/var \
		--enable-shared
	make
}

check() {
	cd "$pkgname-$pkgver"
	make test
}

package() {
	cd "$pkgname-$pkgver"
	make DESTDIR="$pkgdir/" install

	# Keep gem out of pacman-owned dirs, even under sudo
	install -Dm644 /dev/stdin "$pkgdir/etc/gemrc" <<< 'gem: --user-install'
}

