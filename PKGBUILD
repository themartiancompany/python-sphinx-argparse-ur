# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: David Runge <dvzrv@archlinux.org>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_proj="sphinx"
_pkg="${_proj}-argparse"
_Pkg="${_proj}_argparse"
_pkgname="${_pkg}"
pkgname="${_py}-${_pkg}"
_name=sphinx-argparse
_pypi_name=sphinx_argparse
pkgver=0.4.0
pkgrel=3
_pkgdesc=(
  "Sphinx extension that automatically"
  "documents argparse commands and options"
)
arch=(
  any
)
_http="https://github.com"
_ns="ashb"
url="${_http}/${_ns}/${_pkg}"
license=(
  MIT
)
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
  "${_py}-${_proj}"
)
makedepends=(
  python-build
  python-installer
  python-poetry-core
  python-wheel
)
checkdepends=(
  python-pytest
)
optdepends=(
  'python-commonmark: markdown support'
)
_pypi="https://files.pythonhosted.org/packages/source"
source=(
  "${_pypi}/${_pkg::1}/${_pkg}/${_Pkg}-${pkgver}.tar.gz"
)
sha512sums=(
  'b96050da6c02f87c54f9dc9146bed955e99258df740b467575a2b3e9919fa8c4c6d30a736dab24360086bfc0d7d09c4bc7a818700af2c7846eed3a3b99053d65'
)
b2sums=(
  '73118f56ff82d52f04066b9d500aebc77eb5a0fecd03fa69f382c0f2afc0cbffdd395da707cf37b59f039e93935f8d5c3fe0e0f7a2820d3b6509dd78b37b0d74'
)

build() {
  cd \
    "${_Pkg}-${pkgver}"
  "${_py}" \
    -m \
      build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${_Pkg}-${pkgver}"
  pytest \
    -vv
}

package() {
  cd \
    "${_Pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    "dist/"*".whl"
  install \
    -vDm644 \
    "LICENSE" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

# vim:set ts=2 sw=2 et:
