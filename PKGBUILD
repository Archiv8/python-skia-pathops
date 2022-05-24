#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com> and Guillaume Horel <guillaume.horel@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors
# FixMe: Needs proper source build

# Maintainer: Ross Clark <https://github.com/Archiv8/python-skia-pathops/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-skia-pathops/discussions>

_langname="python"
_relname="skia-pathops"

pkgname="${_langname}-${_relname}"
pkgver=0.7.2
pkgrel=2
pkgdesc='Python bindings for the Skia library’s Path Ops (wheel)'
arch=(x86_64)
url="https://github.com/fonttools/skia-pathops"
license=(BSD)
depends=(python)
makedepends=(python-pip)
options=(!strip)
_py=cp310
_wheel="${_relname/-/_}-$pkgver-$_py-$_py-manylinux_2_17_$CARCH.manylinux2014_$CARCH.whl"
source=("https://files.pythonhosted.org/packages/$_py/${_relname::1}/$_relname/$_wheel")
sha256sums=('f6b518fca15b4456ddf99062f334c0333a5165be976fb0c9e071af29128583f7')

# If anybody wants to mess around with the Chromium tree and figure out how to
# build skia from source on Arch I'm open to patches, but even after mucking
# around with ninja and python2 and various patched build toolchains I have
# come up short of a way to build this against Arch packages as dependencies.
# Drop a comment on the AUR page if you have ideas.

package() {
  export PIP_CONFIG_FILE=/dev/null
  pip install --isolated --root="$pkgdir" --ignore-installed --no-deps $_wheel
  python -O -m compileall "$pkgdir"
}
