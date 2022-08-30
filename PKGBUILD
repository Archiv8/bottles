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

# Maintainer: Ross Clark <https://github.com/orgs/Archiv8/bottles/discussions>
# Contributor: Ross Clark <https://github.com/orgs/Archiv8/bottles/discussions>

_relsuffix="brescia-2"

pkgname="bottles"
pkgver=2022.8.28
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
  "711b697eaeb85da827ba9f24ee39f7e309ccdf41e8be633bc0b03715eaf5a16fda4994d59b2915db456a05c87ffa2077d1d71906305011e41000d702326992ab"
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
