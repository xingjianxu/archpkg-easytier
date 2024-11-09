pkgname=easytier
pkgver=2.0.3
pkgrel=3
pkgdesc="A simple, decentralized mesh VPN with WireGuard support."
conflicts=("$pkgname-bin" "$pkgname-git")
arch=("x86_64" "aarch64")
url="https://github.com/EasyTier/EasyTier"
license=('Apache License 2.0')
source=("${pkgname}.service" 
  "${pkgname}.sysusers")
source_x86_64=("$pkgname-$pkgver-x86_64.zip::https://github.com/EasyTier/EasyTier/releases/download/v$pkgver/easytier-linux-x86_64-v$pkgver.zip")
source_aarch64=("$pkgname-$pkgver-aarch64.zip::https://github.com/EasyTier/EasyTier/releases/download/v$pkgver/easytier-linux-aarch64-v$pkgver.zip")
options=('!strip')
sha256sums=('1c77422f897bf5a591d0f5fdb0d436298909f53f6447395cd13fd23d56c44591'
            'dc59c32da7ed31a97547b226a2a3219b7534b1c3a36250c79c6119bf91651d65')
sha256sums_x86_64=('ca9b3b850c066f210ee7a0b93b18a21ce1ed4bf4e4cd9530aee42350286b9cb7')
sha256sums_aarch64=('52d545bcdd3a5a8a069838fae7cdec43d4c2f5166795e75bf5b9bfb07c57d181')
prepare() {
  cd "$srcdir" || exit 1
  if [ "$CARCH" == "x86_64" ]; then
    bsdtar -xf "$pkgname-$pkgver-x86_64.zip" --strip-components=1
  elif [ "$CARCH" == "aarch64" ]; then
    bsdtar -xf "$pkgname-$pkgver-aarch64.zip" --strip-components=1
  fi
}

package() {
  install -Dm644 "${pkgname}.sysusers" "${pkgdir}/usr/lib/sysusers.d/${pkgname}.conf"
	install -Dm644 "${pkgname}.service" "${pkgdir}/usr/lib/systemd/system/${pkgname}.service"
  install -Dm755 "${pkgname}-core" "${pkgdir}/usr/bin/${pkgname}-core"
  install -Dm755 "${pkgname}-cli" "${pkgdir}/usr/bin/${pkgname}-cli"
}
