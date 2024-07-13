# Maintainer: Jonathan Neidel <aur@jneidel.com>

pkgname=nodejs-webpack
pkgver="5.93.0"
pkgrel=1
pkgdesc="JavaScript bundler (CommonJs, AMD, ES6 modules, CSS, Images, JSON, CoffeeScript, LESS)"
arch=(any)
url="https://webpack.js.org/"
license=(MIT)
depends=(nodejs)
makedepends=(npm)
source=("${pkgname}-${pkgver}.tgz::http://registry.npmjs.org/${pkgname#nodejs-}/-/${pkgname#nodejs-}-${pkgver}.tgz")
noextract=("${pkgname}-${pkgver}.tgz")
sha256sums=("3aa06fab2965c33d9b563affe86146bda627b0e872a57ebe94450f17260a9616")

package() {
  # copied from: nodejs-nativefier
  npm install -g --cache "${srcdir}/npm-cache" --prefix "${pkgdir}/usr" "${srcdir}/${pkgname}-${pkgver}.tgz"

  # Fixing permissions
  find "$pkgdir"/usr -type d -exec chmod 755 {} +

  # npm gives ownership of ALL FILES to build user
  # https://bugs.archlinux.org/task/63396
  chown -R root:root "${pkgdir}"

  install -Dm644 "$pkgdir/usr/lib/node_modules/${pkgname#nodejs-}/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
