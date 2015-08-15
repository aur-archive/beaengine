# Maintainer: Nikita Skovoroda <chalkerx@gmail.com>
pkgname=beaengine
rev=175 # released as BeaEngine 4.1 rev 175 on 2013-08-03
#rev=172 # released as BeaEngine 4.1 rev 172 on 2012-01-02
pkgver=4.1r$rev
pkgrel=1
pkgdesc="disassembler library x86 x86-64 (IA32 and Intel64)"
url="http://beaengine.org/"
license=(LGPL3)
arch=('i686' 'x86_64')
depends=('glibc')
makedepends=('cmake' 'svn')
svn="http://beaengine.googlecode.com/svn/trunk/"

build() {
	cd "$srcdir"
	svn co $svn -r $rev sources
	cd "$srcdir/sources"
	cmake -DoptHAS_SYMBOLS=0 -DoptHAS_OPTIMIZED=1 -DoptBUILD_DLL=1 -d .
	make
}
package() {
	cd "$srcdir/sources"
	install -d $pkgdir/usr/lib/
	install -d $pkgdir/usr/include/
	cp -r include/beaengine $pkgdir/usr/include
	install lib/Linux.gnu.release/libBeaEngine.so $pkgdir/usr/lib/
}
