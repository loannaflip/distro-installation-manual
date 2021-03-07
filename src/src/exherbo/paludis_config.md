## Configure Paludis
Edit by executing `vim /etc/paludis/bashrc` and add the following:

```bash
CHOST="x86_64-pc-linux-gnu"
CBUILD="x86_64-pc-linux-gnu"

FLAGS="$(echo {-f{devirtualize-at-ltrans,ipa-pta,lto=1,omit-frame-pointer}, \
-fno-{plt,semantic-interposition,stack-protector},-m{arch,tune}=native} -Ofast -pipe -falign-functions=32)"

export x86_64_pc_linux_gnu="$FLAGS"
export x86_64_pc_linux_gnu_CFLAGS="$FLAGS"
export x86_64_pc_linux_gnu_CXXFLAGS="$FLAGS"
export x86_64_pc_linux_gnu_FFLAGS="$FLAGS"
export x86_64_pc_linux_gnu_FCFLAGS="$FLAGS"
export x86_64_pc_linux_gnu_FDFLAGS="-Wl,-O3 -Wl, -pthread -lpthread"
export x86_64_pc_linux_gnu_LDFLAGS="-Wl,-O3 -Wl,--as-needed -Wl,--sort-common -Wl,--hash-style=gnu"

# Config Protection
CONFIG_PROTECT_MASK="/boot/grub/grub.cfg /etc/environment /etc/resolv.conf /etc/hosts /etc/hostname \
                     /etc/fstab /usr/x86_64-pc-linux-gnu/lib/udev/rules.d /etc/ca-certificates.conf"

# Reduce SPAM from cmake based builds
CMAKE_VERBOSE=OFF

# Lang
LC_ALL="en_US.UTF-8"

# Python breaks with -ffast-math.
if [ "${CATEGORY}/${PN}" = "dev-lang/python" ] ; then
  export x86_64_pc_linux_gnu="$FLAGS -O3"
fi
```

Edit by executing `vim /etc/paludis/options.conf` and add the following:

```bash
*/* -* -recommended_tests -debug systemd gtk alsa bash-completion -bluetooth -wifi threads pulseaudio \
  # N to be replaced with the number of total threads on the system
  BUILD_OPTIONS: jobs=N symbols=strip work=tidyup \
  TARGETS: -* i686-pc-linux-gnu x86_64-pc-linux-gnu \
  PYTHON_ABIS: -* 3.10 \
  INPUT_DRIVERS: -* evdev libinput keyboard mouse \
  LINGUAS: -* en_US \
  # AMD64_CPU_FEATURES: -* TO-BE-FILLED-BY-THE-USER \
  # VIDEO_DRIVERS: -* TO-BE-FILLED-BY-THE-USER \
  PROVIDERS: systemd \
  PARTS: systemd

# Local Use Flags #
sys-apps/paludis -python
dev-scm/git curl
sys-apps/systemd curl
```