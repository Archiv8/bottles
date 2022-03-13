#!/bin/bash

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Francesco Masala <mail@francescomasala.me>
# Contributor:  Francesco Masala <mail@francescomasala.me>
# Contributor: Ross Clark <archiv8@artisteducator.com>


_relsuffix="trento"
_relver="4"

pkgname="bottles"
pkgver=2022.2.28
pkgrel=1
pkgdesc="Easily manage wine and proton prefix"
arch=("any")
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
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/${pkgver}-${_relsuffix}-${_relver}.tar.gz")
sha256sums=(
  "fb54db4114b0abbe8376af4008b6ccd06c41eb2e5d64e372c75f5d2f8e24deff"
  )

build() {
  if [[ -d Bottles ]]; then
        rm -rf Bottles
  fi;
  mv Bottles*/ Bottles/
  cd "Bottles" || exit
  meson --prefix="/usr" build
  ninja -C build
}

package() {
  cd "Bottles" || exit
  DESTDIR="${pkgdir}" ninja -C build install
}
