#Maintainer: Lokawn <39772448+Lokawn@users.noreply.github.com>

pkgbase=plymouth-themes-adi1090x-select
_themenames=(
'pack_1/angular_alt'
'pack_1/black_hud'
'pack_1/circle_flow'
'pack_1/colorful_loop'
'pack_1/cuts'
'pack_1/cuts_alt'
'pack_2/cybernetic'
'pack_2/glitch'
'pack_3/lone'
'pack_3/optimus'
'pack_4/spin')

pkgname=() #initialized by loop at the bottom
pkgver=r28.32a0d92
pkgrel=1
pkgdesc="Select plymouth themes from collection by adi1090x"
arch=('any')
url="https://github.com/adi1090x/plymouth-themes"
license=('GPL')
depends=('plymouth')
makedepends=('git')

source=("git+https://github.com/adi1090x/plymouth-themes.git")
md5sums=('SKIP')

pkgver() {
  cd "plymouth-themes"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

for _themedir in "${_themenames[@]}"
do
    _theme="${_themedir:7}"
    _packdir="${_themedir:0:6}"
    _themename="${_theme//_/-}"
    pkgname+=("plymouth-theme-$_themename-git")
    eval "
package_plymouth-theme-${_theme//_/-}-git() {
    cd \$srcdir/plymouth-themes/${_packdir}/${_theme}
    mkdir -p \$pkgdir/usr/share/plymouth/themes/${_theme}
    find . -type f -exec install -Dm644 \"{}\" \"\${pkgdir}\"/usr/share/plymouth/themes/${_theme}/\"{}\" \\;
}
"
done
