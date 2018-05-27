# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6
pkgver=2.7.1.1
pkgrel=1
pkgdesc="A process supervision suite"
arch=(x86_64)
url="http://skarnet.org/software/s6/"
license=('ISC')
depends=('skalibs' 'execline')
groups=('base' 's6-suite')
conflicts=('s6-git')
source=("$pkgname::git+git://git.skarnet.org/s6#tag=v${pkgver}")
#source=("$pkgname::git+git://git.skarnet.org/s6#commit=$_commit")
#_commit=6ee2e470aa4c66b3477449e7f48343b706c70ddc # tag 2.6.2.0
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd ${srcdir}/${pkgname}
  ./configure --prefix=/usr \
			  --bindir=/usr/bin \
			  --sbindir=/usr/bin \
			  --datadir=/etc
  make
}

package() {
  cd ${srcdir}/${pkgname}

  DESTDIR=${pkgdir} make install
  
  # add doc
  install -dm 0755 $pkgdir/usr/share/doc/$pkgname/
  cp -R doc/* $pkgdir/usr/share/doc/$pkgname/
 
  install -D -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:ft=sh ts=2 sw=2 et:
