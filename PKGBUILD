# Maintainer: Your Name <youremail@domain.com>
pkgname=aliyundrive-webdav
pkgver=1.7.0
pkgrel=1
pkgdesc="阿里云盘 WebDAV 服务"
arch=('x86_64')
provides=('aliyundrive-webdav')
url="https://github.com/messense/aliyundrive-webdav/"
license=('MIT')
depends=('gcc-libs')
makedepends=('cargo')
source=("https://github.com/messense/$pkgname/archive/v$pkgver.tar.gz")
sha256sums=('e04e508c0fb90b7c52a60a19eeb2dc944b95ce8e52a825295198d83455718d6b')

prepare() {
	cd "$pkgname-$pkgver"
	cargo fetch --locked --target "$CARCH-unknown-linux-gnu"
}

build() {
	cd "$pkgname-$pkgver"
	cargo build --frozen --release --all-features
}

# check() {
#     cd "$pkgname-$pkgver"
#     cargo test --frozen --all-features
# }

package() {
	cd "$pkgname-$pkgver"
	install -Dm755 "target/release/${pkgname}" -t "${pkgdir}/usr/bin/"
    install -Dm644 "LICENSE" -t "${pkgdir}/usr/share/licenses/${pkgname}/"
	install -Dm644 "systemd.service" -T "${pkgdir}/usr/lib/systemd/system/$pkgname.service"
}
