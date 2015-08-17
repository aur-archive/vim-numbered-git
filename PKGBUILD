# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-numbered-git
pkgver=20120719
pkgrel=1
pkgdesc="Vim plugin for numbering items in a list"
arch=('any')
depends=('vim')
makedepends=('git')
groups=('vim-plugins')
url="https://github.com/jmcantrell/vim-numbered"
license=('custom:vim')
source=(git+https://github.com/jmcantrell/vim-numbered)
sha256sums=('SKIP')
provides=('vim-numbered')
conflicts=('vim-numbered')
install=vimdoc.install

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing docs...'
  install -Dm 644 README.mkd "$pkgdir/usr/share/doc/vim-numbered/README.mkd"

  msg 'Installing dirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _dir in doc plugin; do
    cp -dpr --no-preserve=ownership $_dir "$pkgdir/usr/share/vim/vimfiles/$_dir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
}
