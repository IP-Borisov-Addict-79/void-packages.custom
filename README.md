# Custom package templates for Void Linux

XBPS templates for packages that are not included in the official Void repositories (and, very likely, will never be included).

Package list:

 - [iso-flag-png](https://github.com/linuxmint/flags): ISO flags collection for Cinnamon desktop (keyboard layout switcher);
 - [JetBrains Mono](https://www.jetbrains.com/lp/mono/): a set of nice monospace fonts from JetBrains;
 - [clhep](https://proj-clhep.web.cern.ch/proj-clhep/): A Class Library for High Energy Physics;
 - [geant4](https://geant4.web.cern.ch/): Toolkit for the simulation of the passage of particles through matter.

## Usage

1. Install XBPS helpers (`xnew`, `xi`, etc.):

   ```
   xbps-install -S xtools
   ```

2. Clone the XBPS source packages collection:
 
   ```
   git clone https://github.com/void-linux/void-packages.git`
   ```
   
   2.1 To allow installing non-free packages, add following line to `etc/conf` file:
   
       ```
       XBPS_ALLOW_RESTRICTED=yes
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

## Building Geant4

1. Build and install `clhep`-related packages:

   ```
   ./xbps-src pkg clhep
   ...
   xi -f clhep-all
   ```
   
2. Add `clhep` - `libCLHEP*.so` mapping to the `common/shlibs` file:

   ```
   libCLHEP-2.4.7.1.so clhep-2.4.7.1_1
   ```

3. Build packages with Geant4 data:

   ```
   find srcpkgs -type d -name "geant4data-*" | cut -d'/' -f2 | while read P; do
       ./xbps-src pkg ${P}
   done
   ```
   
   3.1 Install packages with essential data:
   
       ```
       xi -f geant4data-saiddata geant4data-particlexs geant4data-ensdfstate \
           geant4data-extra geant4data-channeling geant4data-tendl \
           geant4data-radioactivedecay geant4data-pii geant4data-realsurface \
           geant4data-abla geant4data-incl geant4data-emlow \
           geant4data-photonevaporation
       ```

4. Build and install complete set of Geant4:

   ```
   ./xbps-src pkg geant4
   ...
   xi -f geant4-all
   ```
   
5. Optionally: install additional Geant4 data:

   ```
   xi -f geant4data-extra
   ```
   
## Useful links:

- [The XBPS source packages manual](https://github.com/void-linux/void-packages/blob/master/Manual.md)
- [Xbps-src packaging tutorial](https://xbps-src-tutorials.github.io/packaging/index.html)
- [Xbps-src tips and tricks](https://xbps-src-tutorials.github.io/tips-and-tricks.html)
- [SPDX License List](https://spdx.github.io/license-list-data/)
