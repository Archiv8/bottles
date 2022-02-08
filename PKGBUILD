#!/bin/bash

# Maintainer: Francesco Masala <mail@francescomasala.me>
# Contributor:  Francesco Masala <mail@francescomasala.me>
# Contributor: Ross Clark <contact@artisteducator.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154

_relsuffix="trento"
_relver="4"

pkgname="bottles"
pkgver=2022.1.28
pkgrel=1
pkgdesc="Easily manage wine and proton prefix"
arch=("any")
url="https://github.com/bottlesdevs/Bottles"
license=("GPL3")
depends=(
  "hicolor-icon-theme"
  "dconf"
  "python"
  "libhandy"
  "gtk3"
  "patool"
  "p7zip"
  "python-gobject"
  "python-requests"
  "python-yaml"
  "python-markdown"
  "wine"
  "cabextract")
optdepends=(
  "gvfs"
  "vkd3d"
  "lib32-vkd3d"
  "lib32-vulkan-icd-loader"
  "vulkan-icd-loader"
  "gamemode")
makedepends=("meson" "ninja")
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/${pkgver}-${_relsuffix}-${_relver}.tar.gz")
sha256sums=("f4b61d73c4c336477af45814bbb3325e48881e5888242619c8cbb34f82904914")

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
