# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6
pkgver=2.6.1.0
pkgrel=1
pkgdesc="A process supervision suite"
arch=(x86_64)
url="http://skarnet.org/software/s6/"
license=('ISC')
depends=('skalibs' 'execline')
groups=(s6-suite)
conflicts=('s6-git')
source=("$pkgname::git+git://git.skarnet.org/s6#commit=$_commit")
_commit=41e247ca6ab615e58908c4d4a467dee2a7da382a # tag 2.6.1.0
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
