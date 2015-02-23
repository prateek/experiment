# Maintainer: Jon Gjengset <jon@tsp.io>
_gemname=experiment
pkgname=$_gemname-git
pkgver=0.1.0
pkgrel=1
pkgdesc="A tool for running concurrent multi-configuration experiments"
arch=(any)
url="https://github.com/jonhoo/experiment"
license=('GPL')
depends=(ruby) # Full dependency information is available in the yaml specification
makedepends=(rubygems)
source=(https://github.com/jonhoo/$_gemname/archive/v${pkgver}.tar.gz)
md5sums=('2f23320660d713b55f589a060eb38b33')

build() {
  cd "$srcdir/${_gemname}-$pkgver"
  gem build ${_gemname}.gemspec
}

package() {
  cd "$srcdir/${_gemname}-$pkgver"
  # _gemdir is defined inside package() because if ruby[gems] is not installed on
  # the system, makepkg will exit with an error when sourcing the PKGBUILD.
  local _gemdir="$(ruby -rubygems -e'puts Gem.default_dir')"

  gem install --no-user-install --ignore-dependencies -i "$pkgdir$_gemdir" -n "$pkgdir/usr/bin" \
    "$_gemname-$pkgver.gem"
}

# vim:set ts=2 sw=2 et: