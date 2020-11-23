## Configuring Portage
- Fetch the latest snapshot of the Gentoo ebuild repository: `emerge-webrsync`.
- (**OPTIONAL**) Updating the Gentoo ebuild repository: `emerge --sync`.
- Select the desktop profile for the system: `eselect profile set default/linux/amd64/17.1/desktop`.


## Configuring Portage Config
- Edit by executing `nano /etc/portage/make.conf` and add the following:
```bash
# Flags
# if on intel cpu add "-falign-functions=32" in COMMON_FLAGS
COMMON_FLAGS="-O3 -pipe -march=native -mtune=native"
CFLAGS="${COMMON_FLAGS}"
CXXFLAGS="${COMMON_FLAGS}"
FCFLAGS="${COMMON_FLAGS}"
FFLAGS="${COMMON_FLAGS}"
FDFLAGS="-Wl,-O3 -Wl, -pthread -lpthread"
LDFLAGS="-Wl,-O3 -Wl,--as-needed -Wl,--sort-common -Wl,--hash-style=gnu"
# Can be found using https://packages.gentoo.org/packages/app-portage/cpuid2cpuflags
CPU_FLAGS_X86="TO-BE-FILLED-BY-THE-USER"
CHOST="x86_64-pc-linux-gnu"
CBUILD="x86_64-pc-linux-gnu"
# Check https://wiki.gentoo.org/wiki/Category:Video_cards
VIDEO_CARDS="TO-BE-FILLED-BY-THE-USER"

# USE FLAGS
BOOTSTRAP_USE="unicode internal-glib pkg-config split-usr python_targets_python3_7 python_targets_python2_7 -multilib"
USE="-test -fortan -systemd -consolekit -debug -wifi -cups -cdr -ipod -bluetooth -hardened -multilib -samba \
     btrfs ext4 fat elogind unicode dbus man pulseaudio ssl tcmalloc graphite lto xinerama gnome-keyring icu \
     ffmpeg blueray jpeg jpeg2k json openssl alsa pgo jumbo-build gtk X gles2 policykit opengl threads \
     png posix pic rar zip raw quicktime sound ithreads unzip udf secure-delete x264 x265 \
     zeroconf theora 10bit 12bit 7z 7zip mpi-threads offensive bash-completion"


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
- Edit by executing `nano /etc/portage/package.use` and add the following:
```bash
# User Sets #
sys-devel/gcc pgo graphite lto -ada -d -objc
dev-vcs/git curl blksha1
net-libs/nodejs npm
sys-devel/llvm gold
www-client/chromium tcmalloc -hangouts -official -wayland
media-video/ffmpeg openssl fdk
media-libs/mesa vulkan
x11-misc/picom config-file opengl
app-crypt/pinentry gnome-keyring
sys-libs/glibc -multilib
net-print/cups-filters -pdf
app-emulation/qemu usbredir spice
app-emulation/libvirt virt-network virtualbox libvirtd fuse
sys-apps/usermode-utilities fuse
net-dns/dnsmasq script
media-libs/mlt jack frei0r melt kdenlive
app-editors/emacs xft
sys-apps/kmod lzma zlib
dev-qt/qtwidgets gtk
net-misc/spice-gtk usbredir
sys-libs/zlib static-libs
app-editors/vim X terminal
media-libs/libsdl2 haptic
www-client/firefox pgo lto clang custom-optimization gmp-autoupdate hwaccel pulseaudio screenshot startup-notification system-av1 system-icu system-jpeg system-libevent system-libvpx system-sqlite system-webp -bindist -eme-free -geckodriver -jack
dev-lang/rust clippy doc -libressl rls rustfmt -nightly -parallel-compiler -system-bootstrap -wasm
sys-kernel/linux-firmware savedconfig
app-portage/layman sync-plugin-portage git
media-plugins/alsa-plugins pulseaudio
x11-base/xorg-drivers libinput
x11-base/xorg-server elogind xvfb
sys-apps/openrc -netifrc
net-misc/networkmanager -wex
```