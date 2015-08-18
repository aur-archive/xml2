# Contributor: Orivej Desh <masecretaire@gmx.fr>
# Maintainer: Orivej Desh <masecretaire@gmx.fr>
pkgname=xml2
pkgver=0.4
pkgrel=2
pkgdesc="XML/Unix Processing Tools to convert XML and HTML to and from a line-oriented format more amenable to processing by classic Unix pipeline processing tools, like grep, sed, awk, cut, shell scripts, and so forth"
arch=("i686" "x86_64")
url="http://www.ofb.net/~egnor/xml2/"
license=("GPL")
depends=("libxml2")
source=("http://download.ofb.net/gale/$pkgname-$pkgver.tar.gz"
        "01_use_libxml2_instead_of_libxml.patch")
md5sums=('8a0ef16fe0b3e1495307318c590c1ec0'
         '9e810be33d2abbc8aabd8203db1f9654')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  patch -Np1 -i ../01_use_libxml2_instead_of_libxml.patch || return 1
  autoreconf
  ./configure --prefix=/usr
  make || return 1
  make DESTDIR="$pkgdir" install
  cd "$pkgdir/usr/bin"
  rm html2 2html
  ln -s xml2 html2
  ln -s 2xml 2html
}

