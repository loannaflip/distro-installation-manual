## Upgrading the system
- Rebuild all the packages & Update the system's `@world` set: `emerge -qeuvNDU --jobs="$(nproc)" --with-bdeps=y --keep-going @world`.
- Necessary after updating perl-core packages: `perl-cleaner --reallyall -- -av`.
- Check for and rebuild missing libraries: `revdep-rebuild -v`.