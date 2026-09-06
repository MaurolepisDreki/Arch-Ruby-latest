# An up-to-date version of the Ruby interpreter
#
# Maintainer: Nile Aagard <inventerna@gmail.com>
pkgname=ruby
_pkgver="4.0"
pkgver="$_pkgver.6"
pkgrel=1
pkgdesc="Full Ruby $pkgver installation"
url="https://www.ruby-lang.org/en/"
license=('Ruby')
depends=('openssl' 'libyaml' 'zlib')
makedepends=('gcc' 'make')
optdepends=('libffi' 'gmp')
provides=('gem' 'rake' 'irb' 'rdbg' 'bundle' 'bunldler' 'racc' 'rdoc' 'rbs' 'minitest' 'erb')
conflicts=('rubygems' 'ruby-rdoc' 'ruby-rbs' 'ruby-rake' 'ruby-racc' 'ruby-minitest' 'ruby-irb' 'ruby-erb' 'ruby-bundler')
source=("https://cache.ruby-lang.org/pub/$pkgname/$_pkgver/$pkgname-$pkgver.tar.gz")

build() {
	cd "$pkgname-$pkgver"
	./configure
	make
}

check() {
	cd "$pkgname-$pkgver"
	make test
}

package() {
	cd "$pkgname-$pkgver"
	make DESTDIR="$pkgdir/" install
}

