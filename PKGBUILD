# Contributor: solnce <solnce at ratajczak dot one>
# Maintainer: solnce <solnce at ratajczak dot one>
# original code by Sunday87: https://bbs.archlinux.org/viewtopic.php?pid=1253365#p1253365

pkgname=texlive-most-doc
pkgver=20171128
pkgrel=1
pkgdesc="Most TeXLive documentation"
url="http://tug.org/texlive/"
arch=('any')
license=('unknown')
optdepends=('texlive-bin: The texdoc program and some more documentation')
makedepends=('rsync')
install='texlive-most-doc.install'
options=('!strip'  '!purge')
source=(cache-tlpdb.lua)
sha256sums=('be7f87d6e546b09a0795df856175d99b3ae90cec55f3c1f8c0ecbb8349a7fbd1')

build() {
  mkdir -p "$srcdir/usr/share/texmf-dist"
  rsync -av --no-o --no-g --chmod=D755,F644 rsync://tug.org/texlive/Contents/live/texmf-dist/doc "$srcdir/usr/share/texmf-dist/"
}

package() {
  cp -rl "$srcdir"/* "$pkgdir"
  install -D "$startdir"/cache-tlpdb.lua "$pkgdir"/usr/share/texmf-dist/scripts/texdoc/Data.tlpdb.lua
}

post_install() { mktexlsr; }
