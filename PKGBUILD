# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# The following guidelines are specific to BZR, GIT, HG and SVN packages.
# Other git sources are not natively supported by makepkg yet.

# Maintainer: Your Name <youremail@domain.com>
pkgname=filter-types-git
pkgver=v0.1.0.r1.a93359d
pkgrel=1
pkgdesc="command line filterer for files"
arch=('x86_64')
url="https://gitlab.com/mcoffin/filter-files"
license=('GPL')
groups=()
depends=()
makedepends=('git' 'cargo')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
replaces=()
backup=()
options=()
install=
source=('filter-types::git+https://gitlab.com/mcoffin/filter-types.git')
noextract=()
sha512sums=('SKIP')

# Please refer to the 'USING git SOURCES' section of the PKGBUILD man page for
# a description of each element in the source array.

pkgver() {
	cd "$srcdir/${pkgname%-git}"

	# Git, tags available
	printf "%s" "$(git describe --long | sed 's/\([^-]*-\)g/r\1/;s/-/./g')"

	# Git, no tags available
	# printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
	cd "$srcdir/${pkgname%-git}"
}

build() {
	cd "$srcdir/${pkgname%-git}"
	cargo build --release
}

check() {
	cd "$srcdir/${pkgname%-git}"
	cargo test
}

package() {
	cd "$srcdir/${pkgname%-git}"
	install -Dm 0755 -t "$pkgdir"/usr/bin target/release/filter-types
}
