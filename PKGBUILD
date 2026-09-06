# An up-to-date version of the Ruby interpreter
#
# Maintainer: Nile Aagard <inventerna@gmail.com>
pkgname=ruby
_pkgver="4.0"
pkgver="$_pkgver.6"
pkgrel=1
arch=('x86_64')
pkgdesc="Full Ruby $pkgver installation"
url="https://www.ruby-lang.org/en/"
license=('Ruby')
depends=('openssl' 'libyaml' 'zlib')
makedepends=('gcc' 'make')
optdepends=('libffi' 'gmp')
provides=('gem' 'rake' 'irb' 'rdbg' 'bundle' 'bunldler' 'racc' 'rdoc' 'rbs' 'minitest' 'erb')
conflicts=('rubygems' 'ruby-rdoc' 'ruby-rbs' 'ruby-rake' 'ruby-racc' 'ruby-minitest' 'ruby-irb' 'ruby-erb' 'ruby-bundler')
source=("https://cache.ruby-lang.org/pub/$pkgname/$_pkgver/$pkgname-$pkgver.tar.gz")
sha256sums=('837d299e8f7ddf2be31a229a7a7e019d354979825117989acb3b32b1a9be262a')

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

