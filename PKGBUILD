# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.


# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_os="$( \
  uname \
    -o)"
_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_node="nodejs"
if [[ "${_os}" == "Android" ]]; then
  _node="nodejs-lts"
fi
if [[ ! -v "_npm" ]]; then
  _npm="true"
fi
if [[ ! -v "_git_http" ]]; then
  _git_http="github"
fi
if [[ ! -v "_git" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _git="false"
  elif [[ "${_npm}" == "false" ]]; then
    _git="false"
  fi
fi
if [[ ! -v "_docs" ]]; then
  _docs="true"
fi
if [[ ! -v "_archive_format" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _archive_format="tgz"
  elif [[ "${_npm}" == "false" ]]; then
    if [[ "${_evmfs}" == "true" ]]; then
      if [[ "${_git}" == "true" ]]; then
        _archive_format="bundle"
      elif [[ "${_git}" == "false" ]]; then
        _archive_format="tar.gz"
      fi
    elif [[ "${_evmfs}" == "false" ]]; then
      _archive_format="tar.gz"
      if [[ "${_git_http}" == "github" ]]; then
        _archive_format="zip"
      fi
    fi
  fi
fi
_pkg=cert-tools
pkgbase="${_pkg}"
pkgname=(
  "${pkgbase}"
)
if [[ "${_docs}" == "true" ]]; then
  pkgname+=(
    "${pkgbase}-docs"
  )
fi
_pkgdesc=(
  "Native Javascript TLS"
  "(and various other cryptograhic tools)"
  "implementation."
)
pkgdesc="${_pkgdesc[*]}"
pkgver=0.0.8
_commit="d6e838e417a708dbd82baf62e35728a86d4598ac"
_bundle_commit="${_commit}"
pkgrel=1
arch=(
  'any'
)
_http="https://${_git_http}.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${_pkg}"
license=(
  'BSD-3-Clause'
)
depends=(
  "${_node}"
)
provides=(
  "${_node}-${_pkg}=${pkgver}"
)
_cert_tools_docs_optdepends=(
  "${_pkg}-docs:"
    "Certificates Tools"
    "library documentation"
    "and manuals."
)
_cert_tools_docs_ref_optdepends+=(
 "${_pkg}:"
   "the package this documentation"
   "package pertains to."
)
optdepends=(
  "${_cert_tools_docs_optdepends[*]}"
)
if [[ "${_docs}" == "true" ]]; then
  optdepends+=(
  )
fi
makedepends=(
  "npm"
)
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    "git"
  )
fi
if [[ "${_npm}" == "false" ]]; then
  makedepends+=(
  )
fi
if [[ "${_npm}" == "true" ]]; then
  _tag="${pkgver}"
  _tag_name="pkgver"
elif [[ "${_npm}" == "false" ]]; then
  _tag="${_commit}"
  _tag_name="commit"
fi
_tarname="${_pkg}-${_tag}"
_tarfile="${_tarname}.${_archive_format}"
_sum="500e716904c56bd9d3e0930dec23eabfb59b014839ada24725d546c643da8ce5"
_sig_sum="2e5374a4c8abc6c3b469253f5d5a792edb953105baa7f68bceaee3eb7353fa87"
_bundle_sum="4f8cd0089a4be849eee9f1e12e94882d6ddc1991478d02adf8ddbaee25d2febd"
_bundle_sig_sum="01da0d4ed9727e67d4be37571e847a09b5473bf7185e4e81e041b901c58f0b75"
_npm_sum="b3d6643cd490f5d1f42ac4594425a8578536efe045bf8ae08291e47e1fd97c6b"
_npm_sig_sum="75b85412699f1832e4139533a9dce2e1ac3614b401b3b9dccb35c7bbcbc4454b"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
# Kid fren
_evmfs_ns="0x9900e43F7AffF2225C5FFc0Ab133D89B57F3c156"
# Kid
_evmfs_ns="0x926acb6aA4790ff678848A9F1C59E578B148C786"
# Truocolo
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_bundle_uri="${_evmfs_dir}/${_bundle_sum}"
_bundle_src="${_tarfile}::${_evmfs_npm_uri}"
_evmfs_npm_uri="${_evmfs_dir}/${_npm_sum}"
_evmfs_npm_src="${_tarfile}::${_evmfs_npm_uri}"
_evmfs_sig_uri="${_evmfs_dir}/${_sig_sum}"
_evmfs_sig_src="${_tarfile}.sig::${_evmfs_sig_uri}"
_bundle_sig_uri="${_evmfs_dir}/${_bundle_sig_sum}"
_bundle_sig_src="${_tarfile}.sig::${_bundle_sig_uri}"
_npm_sig_uri="${_evmfs_dir}/${_npm_sig_sum}"
_npm_sig_src="${_tarfile}.sig::${_npm_sig_uri}"
_npm_http="http://registry.npmjs.org"
source=()
sha256sums=()
if [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_evmfs_npm_uri}"
    _sum="${_npm_sum}"
    _sig_src="${_npm_sig_src}"
    _sig_sum="${_npm_sig_sum}"
  elif [[ "${_npm}" == "false" ]]; then
    if [[ "${_git}" == "true" ]]; then
      _uri="${_bundle_uri}"
      _sum="${_bundle_sum}"
      _sig_src="${_bundle_sig_src}"
      _sig_sum="${_bundle_sig_sum}"
    elif [[ "${_git}" == "false" ]]; then
      _uri="${_evmfs_uri}"
      _sig_src="${_evmfs_sig_src}"
    fi
  fi
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_npm_http}/${_pkg}/-/${_tarfile}"
  elif [[ "${_npm}" == "false" ]]; then
    _uri="${url}"
  fi
fi
_src="${_tarfile}::${_uri}"
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
if [[ "${_npm}" == "true" ]]; then
  noextract=(
    "${_tarfile}"
  )
fi
validpgpkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

prepare() {
  if [[ "${_evmfs}" == "true" && \
        "${_git}" == "true" ]]; then
    git \
      init \
      "${srcdir}/${_tarname}"
    cd \
      "${_tarname}"
    git \
      "${_git_opts[@]}" \
      remote \
        add \
          origin \
          "${srcdir}/${_tarfile}" || \
      true
    git \
      "${_git_opts[@]}" \
      pull \
        origin \
          "main"
  fi
}

package_cert-tools() {
  local \
    _npm_options=() \
    _find_opts=()
  _npm_options=(
    -g 
    # --cache
    # --user 
    #   root 
    --prefix 
      "${pkgdir}/usr"
  )
  find_opts+=(
    -type
      "d"
    -exec
      chmod
        755
        '{}'
        +
  )
  npm \
    install \
    "${_npm_options[@]}" \
    "${srcdir}/${_pkg}-${pkgver}.tgz"
  rm \
    -fr \
      "${pkgdir}/usr/etc"
  # Fix npm derp
  find \
    "${pkgdir}/usr" \
    "${_find_opts[@]}"
  chown \
    -R \
    "root:root" \
    "${pkgdir}"
  install \
    -vDm644 \
    "${pkgdir}/usr/lib/node_modules/${_pkg}/COPYING" \
    "${pkgdir}/usr/share/licenses/${pkgname}/COPYING"
}

package_cert-tools-docs() {
  local \
    _make_opts=() \
    _copying
  depends=()
  optdepends=(
    "${_cert_tools_docs_ref_optdepends[*]}"
  )
  if [[ "${_npm}" == "true" ]]; then
    _copying="package/COPYING"
    tar \
      xf \
      "${_tarfile}"
    install \
      -vdm755 \
      "${pkgdir}/usr/share/man/man1"
    install \
      -vDm644 \
      "package/man/"* \
      "${pkgdir}/usr/share/man/man1"
  elif [[ "${_npm}" == "false" ]]; then
    _copying="COPYING"
    _make_opts+=(
      DESTDIR="${pkgdir}"
      PREFIX='/usr'
    )
    cd \
      "${_tarname}"
    make \
      "${_make_opts[@]}" \
      install-doc \
      install-man
  fi
  install \
    -vDm644 \
    "${_copying}" \
    "${pkgdir}/usr/share/licenses/${pkgname}/COPYING"
}

