# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-networking
pkgver=2.3.0.2
pkgrel=1
pkgdesc="Small network and client-server tools"
arch=(x86_64)
url="http://skarnet.org/software/s6/"
license=('ISC')
depends=('skalibs' 'execline' 's6' 's6-dns' )
optdepends=('libressl: For build a secure communication tools')
groups=(s6-suite)
conflicts=('s6-networking-git')
source=("$pkgname::git+git://git.skarnet.org/s6-networking#commit=$_commit")
_commit=2b6b20aae8959985a42d100292aac3eca9198165 # tag 2.3.0.2
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

