# Maintainer: Ben Fritsch <ich@abwesend.com>
pkgname=weave-merge
pkgver=0.3.0
pkgrel=1
pkgdesc="Entity-level semantic merge CLI. Resolves conflicts at the function/class level instead of lines."
arch=('x86_64' 'aarch64')
url="https://github.com/Ataraxy-Labs/weave"
license=('MIT' 'Apache-2.0')
depends=(
  'glibc'
  'libgcc'
)
makedepends=('cargo')
source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('6d640e769e084ac08a13032d8d91ecc7c3767ccaa47d12020acc79f450c89ff3')

build() {
    cd "weave-$pkgver"
    unset CFLAGS CXXFLAGS
    cargo build --release --workspace
}

package() {
    cd "weave-$pkgver"
    install -Dm755 "target/release/weave" "$pkgdir/usr/bin/weave"
    install -Dm755 "target/release/weave-driver" "$pkgdir/usr/bin/weave-driver"
    install -Dm755 "target/release/weave-github" "$pkgdir/usr/bin/weave-github"
    install -Dm755 "target/release/weave-mcp" "$pkgdir/usr/bin/weave-mcp"
    install -Dm644 LICENSE-MIT "$pkgdir/usr/share/licenses/$pkgname/LICENSE-MIT"
    install -Dm644 LICENSE-APACHE "$pkgdir/usr/share/licenses/$pkgname/LICENSE-APACHE"
}
