## Configuring Portage
- Fetch the latest snapshot of the Gentoo ebuild repository: `emerge-webrsync`.
- (**OPTIONAL**) Updating the Gentoo ebuild repository: `emerge --sync`.
- Select the desktop profile for the system: `eselect profile set default/linux/amd64/17.1/desktop`.


## Configuring Portage Config
Edit by executing `nano /etc/portage/make.conf` and add the following:
```bash
# Flags
# if you are not on intel cpu then remove "-falign-functions=32" in COMMON_FLAGS
COMMON_FLAGS="-march=skylake -mtune=skylake ${CFLAGS} -pipe -flto='auto' -fdevirtualize-at-ltrans -fno-math-errno -fno-trapping-math -fno-semantic-interposition -fipa-pta -fgraphite-identity -floop-nest-optimize -fuse-linker-plugin -fno-plt -falign-functions=32"
CFLAGS="${COMMON_FLAGS}"
CXXFLAGS="${COMMON_FLAGS}"
FCFLAGS="${COMMON_FLAGS}"
FFLAGS="${COMMON_FLAGS}"
FDFLAGS="-Wl,-O3 -Wl,--as-needed"
LDFLAGS="${FDLAGS}"
DFLAGS="${FDLAGS}"
# Can be found using https://packages.gentoo.org/packages/app-portage/cpuid2cpuflags
CPU_FLAGS_X86="TO-BE-FILLED-BY-THE-USER"
CHOST="x86_64-pc-linux-gnu"
CBUILD="x86_64-pc-linux-gnu"
# Check https://wiki.gentoo.org/wiki/Category:Video_cards
VIDEO_CARDS="TO-BE-FILLED-BY-THE-USER"

# USE FLAGS
BOOTSTRAP_USE="unicode internal-glib pkg-config split-usr python_targets_python3_7 python_targets_python2_7 -multilib"
USE="-test -systemd -consolekit -telemetry -debug -wifi -cups -selinux -samba -cdr -bluetooth -hardened -multilib -samba -wext -modemmanager -minimal \
     luajit X xinerama dbus sound pulseaudio alsa ffmpeg btrfs zstd threads ithreads custom-cflags networkmanager \
     graphite pgo lto posix vaapi openh264 lm-sensors git firmware opengl openal png jpeg raw gif gimp tiff \
     gtk gnome gnome-keyring qt5 wayland unicode vulkan bash-completion gui truetype webp x264 theora encode \
     pdf man aac fftw opus vorbis wavpak tk fish-completion \
     system-av1 system-binutils system-boost system-bootstrap \
     system-cmark system-ffmpeg system-harfbuzz system-heimdal \
     system-icu system-ipxe system-jpeg system-jsoncpp system-lcms \
     system-leveldb system-libevent system-libs system-libvpx \
     system-libyaml system-llvm system-lua system-lz4 \
     system-zstd system-mathjax system-mesa system-mitkrb5 \
     system-numpy system-python system-qemu system-ssl \
     system-webp system-wlroots system-zlib"


# Package specific
SHELL="/bin/bash"
# Check https://wiki.gentoo.org/wiki/Microcode
MICROCODE_SIGNATURES="-s TO-BE-FILLED-BY-THE-USER"
DEFAULT_ABI="amd64"
DISPLAY=":0"
ARCH="amd64"
ABI="amd64"
ABI_X86="64"
LIBDIR_amd64="lib64"
ACCEPT_KEYWORDS="amd64 ~amd64"
ACCEPT_LICENSE="-* @FREE"
ACCEPT_PROPERTIES="*"
ACCEPT_RESTRICT="*"
GRUB_PLATFORMS="efi-64"
CURL_SSL="openssl"
IUSE_IMPLICIT="abi_x86_64 prefix prefix-guest prefix-stack"
KERNEL="linux"
USERLAND="GNU"
ELIBC="glibc"
GSETTINGS_BACKEND="dconf"
INPUT_DEVICES="libinput"
MANPAGER="manpager"

# Protection
CONFIG_PROTECT="/boot/grub/grub.cfg /etc /etc/environment /etc/fstab /etc/hostname /etc/hosts /etc/resolv.conf \
                /usr/share/config /usr/share/gnupg/qualified.txt"
CONFIG_PROTECT_MASK="/etc/ca-certificates.conf /etc/dconf /etc/env.d /etc/fonts/fonts.conf /etc/gconf \
                     /etc/gentoo-release /etc/revdep-rebuild /etc/sandbox.d /etc/terminfo"
COLLISION_IGNORE="/lib/modules/*"
UNINSTALL_IGNORE="/lib/modules/* /var/run /var/lock"

# Miscellaneous
I_KNOW_WHAT_I_AM_DOING=y
USER="root"
TERM="xterm-256color"
COLORTERM="truecolor"
FEATURES="-news -test -fakeroot fail-clean assume-digests binpkg-docompress binpkg-dostrip binpkg-logs candy \
          preserve-libs config-protect-if-modified distlocks ebuild-locks fixlafiles ipc-sandbox merge-sync \
          multilib-strict network-sandbox parallel-fetch parallel-install pid-sandbox sandbox \
          protect-owned qa-unresolved-soname-deps sfperms strict unknown-features-warn \
          unmerge-logs unmerge-orphans userfetch userpriv usersandbox usersync xattr"
CALLIGRA_FEATURES="karbon sheets words"
BINPKG_COMPRESS="bzip2"
LESS="-R -M --shift 5"
LESSOPEN="|lesspipe %s"
PORTAGE_VERBOSE="1"
EMERGE_WARNING_DELAY="2"
CLEAN_DELAY="0"
PORTAGE_DEBUG="0"
NOCOLOR="false"
AUTOCLEAN="yes"
EMERGE_DEFAULT_OPTS="--ask --deep --tree --verbose --complete-graph=y --verbose-conflicts \
                     --with-bdeps=y --quiet-build=y --keep-going=y"
# N to be replaced with the number of total threads on the system
MAKEOPTS="-jN --no-print-directory"
PORTAGE_NICENESS="-5"
ROOT="/"
SYSROOT="/"
LOGNAME="root"
HOME="/root"
EROOT="/"
ESYSROOT="/"
GPSD_PROTOCOLS="ashtech aivdm earthmate evermore fv18 garmin garmintxt gpsclock greis isync itrax mtk3301 nmea \
                ntrip navcom oceanserver oldstyle oncore rtcm104v2 rtcm104v3 sirf skytraq superstar2 \
                timing tsip tripmate tnt ublox ubx"
PORTAGE_RSYNC_OPTS="--recursive --links --safe-links --perms --times --omit-dir-times --compress \
                    --force --whole-file --delete --stats --human-readable --timeout=180 \
                    --exclude=/distfiles --exclude=/local --exclude=/packages --exclude=/.git"
FETCHCOMMAND="wget -t 3 -T 60 --passive-ftp -O "${DISTDIR}/${FILE}" "${URI}""
FETCHCOMMAND_RSYNC="rsync -LtvP "${URI}" "${DISTDIR}/${FILE}""


# Portage Hierarchy
PORTAGE_TMPDIR="/var/tmp"
PORTAGE_CONFIGROOT="/"
PORTAGE_DEPCACHEDIR="/var/cache/edb/dep"
PORTDIR="/var/db/repos/gentoo"
DISTDIR="/var/cache/distfiles"
PKGDIR="/var/cache/binpkgs"
PORTAGE_LOGDIR="/var/log/portage"

# Language
LINGUAS="en en_US"
LANG="en_US.UTF8"
LC_ALL="en_US.UTF-8"
LC_MESSAGES=C

# Mirrors
GENTOO_MIRRORS="http://distfiles.gentoo.org"
```
Edit by executing `nano /etc/portage/package.use` and add the following:
```bash
# User Sets #
sys-devel/gcc pgo graphite lto custom-cflags valgrind jit zstd
sys-libs/glibc custom-cflags
sys-devel/binutils multitarget
net-libs/nodejs npm inspector
sys-devel/llvm gold llvm_targets_WebAssembly
media-video/ffmpeg openssl fdk
x11-misc/picom config-file opengl
app-emulation/qemu usbredir spice xen
app-emulation/libvirt virt-network virtualbox libvirtd fuse
sys-apps/usermode-utilities fuse
app-editors/emacs xft athena
www-client/chromium official custom-cflags
www-client/firefox pgo lto custom-optimization gmp-autoupdate hwaccel pulseaudio -screenshot -startup-notification -bindist eme-free -geckodriver -jack
dev-lang/rust clippy miri doc -libressl rls rustfmt nightly parallel-compiler system-bootstrap wasm llvm_targets_WebAssembly
sys-kernel/linux-firmware savedconfig
app-portage/layman sync-plugin-portage git
x11-base/xorg-drivers libinput
x11-base/xorg-server elogind xvfb kdrive xephyr
net-misc/networkmanager -wext -modemmanager
media-plugins/alsa-plugins pulseaudio
media-fonts/nerd-fonts noto
media-video/mpv libmpv
sys-boot/grub fonts truetype mount
sys-apps/systemd zstd cgroup-hybrid
media-libs/vulkan-loader layers
app-office/libreoffice java
media-fonts/noto extra
media-fonts/powerline-fonts sourcecodepro
media-fonts/cantarell font_types_otf
media-sound/deadbeef clang
app-emulation/xen efi
app-emulation/xen-tools system-ipxe -system-qemu qemu -ipxe
sys-boot/plymouth -udev
x11-wm/openbox imlib
gui-wm/sway fish-completion man swaybar swaybg swayidle swaymsg swaylock swaynag tray wallpapers zsh-completion
sys-apps/openrc -netifrc
net-misc/networkmanager -wex
```