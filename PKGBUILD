# Maintainer: Florian Bruhin (The Compiler) <archlinux.org@the-compiler.org>

pkgname=python-quick2wire
pkgver=20130523
pkgrel=1
pkgdesc="Python API for controlling GPIO and I2C devices connected to the Raspberry Pi"
arch=(any)
url="https://github.com/quick2wire/quick2wire-python-api"
license=('MIT' 'LGPL')
depends=('python' 'python-distribute')
options=('!emptydirs' '!strip')

_gitroot='https://github.com/quick2wire/quick2wire-python-api.git'
_gitname='quick2wire'

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"

  cd "${srcdir}/$_gitname-build"
  rm -rf build

  python setup.py build  
}

package() {
  cd "${srcdir}/$_gitname-build"
  python setup.py install --root="${pkgdir}" --optimize=1
}

# vim:set ts=2 sw=2 et:
