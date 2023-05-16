# Maintainer: Rudra Saraswat <rs2009@ubuntu.com>

pkgname='akshara-git'
pkgver=r33.e380b80
pkgrel=2
pkgdesc="An update system for operating systems"
arch=('x86_64' 'i686')
url="https://github.com/blend-os/blend"
license=('GPL3')
makedepends=("electron${_electronversion}" 'git' 'npm' 'base-devel')
source=('git+https://github.com/blend-os/akshara.git')
sha256sums=('SKIP')

depends=('bash' 'python' 'python-lockfile' 'python-psutil' 'python-fasteners' 'squashfs-tools' 'p7zip' 'zsync')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")

pkgver() {
    cd "${srcdir}/${pkgbase%-git}"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
    cd "${srcdir}/${pkgbase%-git}"
    install -Dm755 \
        "${pkgname%-git}" \
        -t "${pkgdir}"/usr/bin/
    install -Dm644 "${pkgname%-git}.service" -t \
        "${pkgdir}"/usr/lib/systemd/system/
    install -Dm644 "${pkgname%-git}.hook" \
        "${pkgdir}/usr/lib/initcpio/hooks/${pkgname%-git}"
    install -Dm644 "${pkgname%-git}.install" \
        "${pkgdir}/usr/lib/initcpio/install/${pkgname%-git}"
}
