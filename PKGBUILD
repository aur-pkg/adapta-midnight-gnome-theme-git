# Maintainer: Nicholas Atkins <nbatkins@gmail.com>

pkgname=adapta-midnight-gtk-theme-git
pkgver=3.95.0.1
outdir=src

# Output Paths
# SRCDEST=$outdir/src
PKGDEST=$outdir
pkgrel=1
pkgdesc='An adaptive Gtk+ theme based on Material Design Guidelines'
arch=('any')
url='https://github.com/gtk-themes/adapta-midnight'
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
source=('git+https://github.com/gtk-themes/adapta-midnight.git')
sha256sums=('SKIP')

pkgver() {
  cd adapta-midnight

  git describe --always | sed -E 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd adapta-midnight

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
  cd adapta-midnight

  make DESTDIR="${pkgdir}" install

  install -dm 755 "${pkgdir}"/usr/share/plank/themes
  ln -s /usr/share/themes/Adapta/plank "${pkgdir}"/usr/share/plank/themes/Adapta
}

# vim: ts=2 sw=2 et: