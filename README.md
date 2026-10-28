# Custom package templates for Void Linux

Some packages absent from official Void repositories.

Contents:

 - iso-flag-png: ISO flags collection for Cinnamon desktop (<https://github.com/linuxmint/flags>)
 - TBD.

## Usage

1. Clone the XBPS source packages collection:
 
   ```
   git clone https://github.com/void-linux/void-packages.git`
   ```
   
2. Bootstrap the `masterdir`:

   ```
   cd void-packages
   ./xbps-src binary-bootstrap`
   ```
   
3. Copy custom package templates to void-packages source-tree

   ```
   cp -r ../void-packages.custom/srcpkgs/* srcpkgs
   ```
   
4. Build and install desired packages:

   ```
   ./xbps-src pkg iso-flag-png
   xi -f iso-flag-png
   ```

## Useful links:

- [The XBPS source packages manual](https://github.com/void-linux/void-packages/blob/master/Manual.md)
- [Xbps-src packaging tutorial](https://xbps-src-tutorials.github.io/packaging/index.html)
