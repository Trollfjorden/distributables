# Changelog

## [Unreleased] - 2026-01-02

### Added
- **Debian 13 (Trixie) Support**:
    - Updated `riven.sh` to default to Debian 13.
    - Updated `build.func` to include Debian 13 in the OS selection menu.
    - Removed restrictions forcing Riven to Debian 12.

### Fixed
- **Verbose Logging**:
    - Replaced silent `> /dev/null` redirection with `$STD` variable for `pnpm` commands in `riven-install.sh`.
    - Enables debugging of frontend build failures when "Verbose" mode is selected.
- **Frontend Build Memory**:
    - Added `NODE_OPTIONS="--max-old-space-size=6144"` to `riven-install.sh`.
    - Fixes `JavaScript heap out of memory` errors during `pnpm run build` by allowing Node.js to use up to 6GB RAM.
- **Frontend Service**:
    - Fixed invalid `ExecStart` syntax in `riven-frontend.service` (removed broken `ORIGIN=${ORIGIN}` prefix).
    - Ensures the systemd service starts correctly after installation.
- **Default Install Logic**:
    - Restored missing `default_settings` function in `build.func`.
    - Updated `install_script` to explicitly prompt "Use Default Settings?" allowing a One-Click install experience.
- **Branding**:
    - Removed third-party `tteck` branding and personal donation links from the container description.
    - Replaced branding with Riven GitHub repository link.

### Changed
- **Testing Configuration**:
    - Updated `riven.sh` to fetch `build.func` from fork (`Trollfjorden/distributables`).
    - Updated `build.func` to fetch `create_lxc.sh` and `install.func` from fork (`Trollfjorden/distributables`).
    - *Note*: These URL changes are for testing purposes and should be reverted before upstreaming.
