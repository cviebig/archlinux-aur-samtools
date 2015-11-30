# Maintainer: Christian Krause ("wookietreiber") <kizkizzbangbang@googlemail.com>
# Contributor: Markus Heuser <markus.heuser@web.de>

pkgname=samtools
pkgver=0.1.19
pkgrel=1
pkgdesc="tools for manipulating next-generation sequencing data"
arch=('i686' 'x86_64')
url="http://www.htslib.org/"
license=('custom')
depends=('perl' 'htslib')
optdepends=('luajit: needed for r2plot.lua vcfutils.lua'
            'python2: needed for varfilter.py')
options=('staticlibs')
source=($pkgname-$pkgver.tar.bz2)
md5sums=('ff8b46e6096cfb452003b1ec5091d86a')

prepare() {
  cd $srcdir/$pkgname-$pkgver


  sed -i 's/CFLAGS=		-g -Wall -O2/CFLAGS= -g -Wall -O2 -fPIC -DPIC/g' Makefile

  sed -e 's|#!/usr/bin/env python|#!/usr/bin/env python2|' \
      -i misc/varfilter.py

}

build() {
  cd $srcdir/$pkgname-$pkgver

  make
}

check() {
  cd $srcdir/$pkgname-$pkgver

}

package() {
  cd $srcdir/$pkgname-$pkgver

  install -d $pkgdir/usr/include/samtools
  install -Dm644 *.h $pkgdir/usr/include/samtools

  install -Dm644 libbam.a $pkgdir/usr/lib/libbam.a

}
