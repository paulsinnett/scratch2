# Maintainer: Amiad Bareli <amiad@hatul.info>

pkgname=scratch2
_ver=454
pkgver="2.0.$_ver"
pkgrel=2
pkgdesc="With Scratch, you can program your own interactive stories, games, and animations"
arch=('any')
url="https://scratch.mit.edu"
license=('GPL')
depends=('adobe-air' 'libxt' 'libxtst' 'alsa-lib')
depends_x86_64+=('lib32-libxt' 'lib32-libxtst' 'lib32-alsa-lib')
makedepends=('unzip')
source=("https://scratch.mit.edu/scratchr2/static/sa/Scratch-$_ver.air" "$pkgname.desktop" "$pkgname.png" "$pkgname.xml" "x-$pkgname-project.png")
sha1sums=('c096866c40c63f36ccf11539433eb7ae66797adf'
			'54d603c20b35daa24a700fec465e6cc3b2645406'
			'bfca77daa1a9079f2197d98509ca4a33b3246df1'
			'2d45707fd12c709e21fa74b85f6c7b7dfe0d47a2'
			'211b6b6ca9e987327632446f1bb15908babbcfae')
noextract=("Scratch-$_ver.air")

package() {
  mkdir $srcdir/$pkgname
  unzip Scratch-$_ver.air -d $srcdir/$pkgname

  install -dm 755 $pkgdir/opt/airapps/
  cp -r $srcdir/$pkgname $pkgdir/opt/airapps/$pkgname
  chmod -R 755 $pkgdir/opt/airapps/$pkgname

  install -dm 755 $pkgdir/usr/bin
  echo "#!/bin/bash" >> $pkgdir/usr/bin/$pkgname
  echo "/opt/adobe-air-sdk/bin/adl -nodebug /opt/airapps/$pkgname/META-INF/AIR/application.xml /opt/airapps/$pkgname/ -- \"\$1\"" >> $pkgdir/usr/bin/$pkgname
  chmod 755 $pkgdir/usr/bin/$pkgname

  install -Dm 644 "$pkgname.desktop" $pkgdir/usr/share/applications/$pkgname.desktop
  install -Dm 644 "$pkgname.xml" $pkgdir/usr/share/mime/packages/$pkgname.xml
  install -Dm 644 "$pkgname.png" $pkgdir/usr/share/pixmaps/$pkgname.png
  install -Dm 644 "x-$pkgname-project.png" $pkgdir/usr/share/pixmaps/x-$pkgname-project.png
}
