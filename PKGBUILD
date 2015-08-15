# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# See http://wiki.archlinux.org/index.php/VCS_PKGBUILD_Guidelines
# for more information on packaging from GIT sources.

# Maintainer: Shawn Siefkas <shawn@siefk.as>
pkgname=dotcloud-docker-git
pkgver=v0.1.4.51.g1ec6c22
pkgrel=1
pkgdesc="Docker - the Linux container runtime"
arch=('x86_64')
url="https://github.com/dotcloud/docker"
license=('Apache License 2.0')
depends=('bridge-utils' 'iproute2' 'aufs3' 'go')
makedepends=('git' 'go')
provides=('dotcloud-docker')
source=('docker::git+https://github.com/dotcloud/docker.git')
conflicts=('dotcloud-docker')
md5sums=('SKIP')

build() {
  export GOPATH="$srcdir/gopath"
  cd docker
  make
}

package() {
  cd docker
  mkdir -p "$pkgdir/usr/sbin"
  cp bin/docker "$pkgdir/usr/sbin"
}

pkgver() {
  cd docker
  git describe --always | sed 's|-|.|g'
}

# vim:set ts=2 sw=2 et:
