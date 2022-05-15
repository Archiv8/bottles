#!/bin/bash

# Created from the original AUR package by Francesco Masala, "mail@francescomasala.me"

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

# Maintainer: Ross Clark <archiv8@artisteducator.com>
# Contributor: Ross Clark <archiv8@artisteducator.com>

_relsuffix="trento"

pkgname="bottles"
pkgver=2022.5.14
pkgrel=1
pkgdesc="Easily manage wine and proton prefix"
arch=(
  "any"
)
url="https://github.com/bottlesdevs/Bottles"
license=("GPL3")
depends=(
  # Official Arch Linux repositories
  "cabextract"
  "dconf"
  "gtksourceview3"
  "gtksourceview4"
  "gtk3"
  "hicolor-icon-theme"
  "libhandy"
  "lib32-gnutls"
  "python"
  "python-gobject"
  "python-markdown"
  "python-requests"
  "python-yaml"
  "p7zip"
  "webkit2gtk"
  "wine"
  "xorg-xdpyinfo"

  # Archiv8 packages
  "patool"
)
optdepends=(
  # Official Arch Linux repositories
  "gamemode"
  "gvfs"
  "lib32-vkd3d"
  "lib32-vulkan-icd-loader"
  "vkd3d"
  "vulkan-icd-loader"

)
makedepends=(
  # Official Arch Linux repositories
  "meson"
  "ninja"
)
source=(
  "${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/${pkgver}-${_relsuffix}.tar.gz"
)
sha512sums=(
  "83947ccb69258170c4fbf3594decb6658e8893ed5e4a80fd8cc05319592b89ee984bd0c8d443694dfe7040dbe21f8cd325e6cd50f0d3bd5422fd2a18cfd1fe92"
)

build() {

  if [[ -d Bottles ]]; then
    rm -rf Bottles
  fi

  mv Bottles*/ Bottles/
  cd "Bottles" || exit

  meson --prefix="/usr" build

  ninja -C build
}

package() {

  cd "Bottles" || exit

  DESTDIR="${pkgdir}" ninja -C build install
}
