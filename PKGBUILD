# Maintainer: Nicholas Atkins <nbatkins@gmail.com>

pkgname=adapta-midnight-gtk-theme-git
pkgver=3.92.2.63
pkgrel=1
pkgdesc='An adaptive Gtk+ theme based on Material Design Guidelines'
arch=('any')
url='https://github.com/appkins/adapta-midnight-gtk-theme'
license=('GPL2')
depends=('gtk-engine-murrine' 'gtk3')
makedepends=('git' 'gnome-shell' 'inkscape' 'libxml2' 'parallel' 'sassc')
optdepends=('gnome-shell: The GNOME Shell'
            'gnome-flashback: The GNOME flashback shell'
            'budgie-desktop: The Budgie desktop'
            'cinnamon: The Cinnamon desktop'
            'xfdesktop: The Xfce desktop')
provides=('adapta-midnight-gtk-theme')
conflicts=('adapta-midnight-gtk-theme')
source=('git+https://github.com/appkins/adapta-midnight-gtk-theme.git')
sha256sums=('SKIP')

pkgver() {
  cd adapta-midnight-gtk-theme

  git describe --tags | sed 's/-/.r/; s/-g/./'
}

build() {
  cd adapta-midnight-gtk-theme

  #bundle install --path .
  #export PATH="$(find $PWD/ruby -maxdepth 2 -type d -name bin):$PATH"

  ./autogen.sh \
    --prefix='/usr' \
    --enable-parallel \
    --enable-chrome \
    --enable-plank \
    --enable-telegram \
    --disable-unity
  make
}

package() {
  cd adapta-midnight-gtk-theme

  make DESTDIR="${pkgdir}" install

  install -dm 755 "${pkgdir}"/usr/share/plank/themes
  ln -s /usr/share/themes/Adapta/plank "${pkgdir}"/usr/share/plank/themes/Adapta
}

# vim: ts=2 sw=2 et:

