# Mainainer: Sébastien "Seblu" Luttringer <seblu@archlinux.org>
# Contributor: Allan McRae <allan@archlinux.org>
# Contributor: judd <jvinet@zeroflux.org>

pkgname=gzip
pkgver=1.11
pkgrel=1
pkgdesc='GNU compression utility'
arch=('x86_64')
url='https://www.gnu.org/software/gzip/'
license=('GPL3')
groups=('base-devel')
depends=('glibc' 'bash' 'less')
validpgpkeys=('155D3FC500C834486D1EEA677FD9FCCB000BEEEE') # Jim Meyering
source=("https://ftp.gnu.org/pub/gnu/gzip/gzip-$pkgver.tar.xz"{,.sig})
md5sums=('d1e93996dba00cab0caa7903cd01d454'
         'SKIP')
prepare() {
  cd $pkgname-$pkgver
  # apply patch from the source array (should be a pacman feature)
  local filename
  for filename in "${source[@]}"; do
    if [[ "$filename" =~ \.patch$ ]]; then
      msg2 "Applying patch ${filename##*/}"
      patch -p1 -N -i "$srcdir/${filename##*/}"
    fi
  done
  :
}

build() {
  cd $pkgname-$pkgver
  ./configure --prefix=/usr
  make
}

check() {
  cd $pkgname-$pkgver
  make check
}

package() {
  cd $pkgname-$pkgver
  make prefix="$pkgdir/usr" install
}

# vim:set ts=2 sw=2 et:
