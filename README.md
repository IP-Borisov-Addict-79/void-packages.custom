# Custom package templates for Void Linux

XBPS templates for packages that are not included in the official Void repositories (and, very likely, will never be included).

Package list:

 - [iso-flag-png](https://github.com/linuxmint/flags): ISO flags collection for Cinnamon desktop (keyboard layout switcher);
 - [JetBrains Mono](https://www.jetbrains.com/lp/mono/): a set of nice monospace fonts from JetBrains;
 - [clhep](https://proj-clhep.web.cern.ch/proj-clhep/): A Class Library for High Energy Physics. **The XBPS source packages manual** insists that [_...libraries have to be split into two sub packages: `<name>` and `<name>-devel`_](https://github.com/void-linux/void-packages/blob/master/Manual.md#libs). But since no sane person interested in HEP-related computations would install only runtime part of CLHEP while skipping the development-related bits, a meta-package was created that would pull-up both runtime and development files as dependencies:
     - clhep-all: installs runtime and development files,
     - clhep-devel: development files;
 - clhep-doc: documentation for CLHEP;
 - _TBD..._

## Usage

1. Install XBPS helpers (`xnew`, `xi`, etc.):

   ```
   xbps-install -S xtools
   ```

2. Clone the XBPS source packages collection:
 
   ```
   git clone https://github.com/void-linux/void-packages.git`
   ```
   
3. Bootstrap the `masterdir`:

   ```
   cd void-packages
   ./xbps-src binary-bootstrap`
   ```
   
4. Copy custom package templates to void-packages source-tree

   ```
   cp -r PATH-TO/void-packages.custom/srcpkgs/* srcpkgs
   ```
   
5. Build and install the desired packages:

   ```
   ./xbps-src pkg iso-flag-png
   ...
   xi -f iso-flag-png
   ```

## Useful links:

- [The XBPS source packages manual](https://github.com/void-linux/void-packages/blob/master/Manual.md)
- [Xbps-src packaging tutorial](https://xbps-src-tutorials.github.io/packaging/index.html)
- [Xbps-src tips and tricks](https://xbps-src-tutorials.github.io/tips-and-tricks.html)
- [SPDX License List](https://spdx.github.io/license-list-data/)
