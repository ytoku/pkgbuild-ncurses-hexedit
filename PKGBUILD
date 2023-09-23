# Maintainer: ytoku
pkgname=ncurses-hexedit
_progver=0.9.7
pkgver="0.9.7+orig_7.2"
pkgrel=1
epoch=
pkgdesc="[N] Curses Hexedit: a full screen hex editor using the ncurses library."
arch=(x86_64 i686 pentium4 armv7h aarch64)
url="http://www.rogoyski.com/adam/programs/hexedit/"
license=('GPL')
groups=()
depends=(ncurses)
makedepends=(autoconf automake texinfo)
checkdepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
# Patches from https://sources.debian.org/patches/ncurses-hexedit/0.9.7+orig-7.2/
_patches=(
  rename_binaries.patch
  hexedit_lsm.patch
  printf_is_a_macro.patch
  fix_its_typo.patch
  allow_white_space.patch
  hurd_path_max.patch
  help_screen_typo.patch
  fix_search_on_64bit_sys.patch
  fix_hexedit_references.patch
  fix_segfault.patch
  autoconf_2.69.patch
  fix_conflicting_definitions.patch
  info_dir_section.patch
  fix_compilation_warnings.patch
  quit_immediately_if_unmodified.patch
  enforce_readonly_mode.patch
  fix_buffer_overruns.patch
  fix_spelling_errors.patch
  gcc_10.patch
  ncurses.patch
)
source=(
  "http://www.rogoyski.com/adam/programs/hexedit/hexedit-$_progver.tar.gz"
  ${_patches[@]}
)
noextract=()
sha256sums=('3d15ab33dae9014180cc3d54636aaab4d9c88257f7a2d1cfda490d1bfa6e043a'
            '67ac59626cd4a442c110e04f74261765113ec39e576bb736fbcee5a60f06f0fd'
            '742de93c472c315c7ef622203cf77e68a406e6982f7bb7d00d9ce34969ab84eb'
            '633dd778d73755294ca87c6c13e1154bed723c915b77fe88d6908018fb649cbd'
            'c2438e4f54f64f50ba90203c115030a4a24d6cf01fadfb59c9fbd69d54e968ff'
            '45c78cd6f424bd6c3a658dc90b4193c5990abf00aa03aa4ec6d8250222e91178'
            '8ed6074b9441e01d3490e76f2bc917d5fa32e73cc419ed54bbe201be0788b764'
            'bed886e5fd7f4e6889ddb67e0f03f54929fdcc119b7f8eb4a46de5110c1750ce'
            'a681cd2973eb2cbfeb8c1b46d6de20b4fdb687edc9fa37f444166189fd1d72fe'
            '984a05c93110d5a1a75fe78197ca530a98f294be9c7db1bc60174a6394cc4adb'
            '1d4d3f2a5abd8a3a74249e3a662059327f8b6b57b35387a47d0f9e504868dd58'
            'c156c0685ca50fe3fe6e04ab8dfa586420561abf73f9a3d179eb20156352c94f'
            '7be6377ebc6d109f5f62b1f5e4d5b0bc3ed60d91b42db1044d4288029eea658c'
            '570adf8f9105f960c0d5bf5727d879db73b6920ca2658723771f7fea6487e76c'
            '6781a53b160b4c9dcfee9777a90915b464b40c454aa90d84aba29c6c40b14978'
            'f178f045c2fc5721cff76ac4ba5d3eec7e378282deb58f370494c4bf3ee28a46'
            '2a7eac9b559e2b783869d61dd48f4f99828e86a39ed0f381e15db8d3d95054bd'
            '9cda8c490f58ee86f2264d34e5b4933c2e9edac4049cc5b9e73f4ed0b9e9d89d'
            '5a911608db2b99755f55abbf15af03372c6b1ce896e5694b4360714e0c3b0cf2'
            'db795137a1882259dfff65f65454cda6b0be1814bb5076b7f4b9dd3a0ab8b25d'
            '09b293332b76e78a7af5b13a2d15d4155ab8655543a4a7af9bcf985101a1f6cc')

prepare() {
  cd "hexedit-$_progver"
  for _patch in ${_patches[@]}; do
    patch -p1 -i "$srcdir/$_patch"
  done
}

build() {
  cd "hexedit-$_progver"
  autoreconf -f -i
  ./configure --prefix=/usr
  make
}

package() {
  cd "hexedit-$_progver"
  make prefix="$pkgdir/usr/" install
}
