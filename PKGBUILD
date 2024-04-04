# Maintainer: Robert Peters <ropeters@pm.me>

pkgname=vorta-rp
_pkgname=vorta
pkgver=v0.9.1
pkgrel=1
pkgdesc="A GUI for BorgBackup"
arch=('any')
url="https://github.com/borgbase/vorta"
license=('GPL-3.0')
provides=('vorta')
conflicts=('vorta')
depends=('borg' 'python-appdirs' 'python-pyqt6' 'python-peewee' 'python-paramiko' 'python-dateutil' 'python-secretstorage' 'python-psutil' 'python-llfuse' 'python-setuptools')
makedepends=('qt5-tools' 'python-pip' 'git')
options=(!emptydirs)
source=("$pkgname"::"https://github.com/borgbase/${_pkgname}/archive/${pkgver}.tar.gz")
sha256sums=('0f627c2464bf1631711151464fe1ea59781f0c91a76cf5a081a5797a897f2929')

build() {
  cd "${srcdir}/vorta-0.9.1"
  make translations-to-qm
  python setup.py build
}

package() {
  cd "${srcdir}/vorta-0.9.1"
  export PYTHONHASHSEED=0
  python setup.py install --root="$pkgdir" --optimize=1 --skip-build
  install -Dm644 package/icon-symbolic.svg \
    "$pkgdir/usr/share/icons/hicolor/symbolic/apps/com.borgbase.Vorta-symbolic.svg"
  install -Dm644 "src/$_pkgname/assets/metadata/com.borgbase.Vorta.appdata.xml" -t \
    "$pkgdir/usr/share/metainfo"
  install -Dm644 "src/$_pkgname/assets/metadata/com.borgbase.Vorta.desktop" -t \
    "$pkgdir/usr/share/applications"
}
