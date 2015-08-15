pkgname=goja
pkgver=20141110
pkgrel=1
pkgdesc="FHDW GOJA educational IDE"
url="http://ux-02.ha.bib.de/daten/Löwe/GOJA/"
license=('custom')
depends=('java-runtime')
optdepends=('oracle-xe: database support')
arch=('any')
source=("${url}Goja${pkgver}.jar"
"${url}/JARS/ojdbc14.jar"
"${url}/JARS/regExp20130422.jar"
"${url}/JARS/xmlrpc-1.2-b1ML20130422.jar"
\
'goja.desktop' 'icon.png' 'goja.launcher')

md5sums=('d25915328588227cd777651ecc74c970'
         'a28ee417a523434db522fe593a41d7d0'
                  '3c022085955bba3d14da64fd2af0a26b'
                           'b7b08e8c7c55e39fd5bb1abb0c6d1152'
                                    'fc60973cbdc1349d9a5471b5a9a72960'
                                             'b654b6f4fad897726e29a47f5879cc13'
                                                      'e4d130f9b07dbe243609258d71f76a83')

  package() {
    cd ${srcdir}

    # Create Destination Directories
    install -d ${pkgdir}/{usr/{bin/,share/java/},opt/${pkgname}/JARS/}

    # Install program
    install -D -m644 ${srcdir}/Goja${pkgver}.jar \
        ${pkgdir}/opt/${pkgname}/${pkgname}.jar

    # Install deps
    for jar in ojdbc14.jar regExp20130422.jar xmlrpc-1.2-b1ML20130422.jar
    do
      install -D -m644 ${srcdir}/$jar \
        ${pkgdir}/opt/${pkgname}/JARS/$jar

      # Symlink dep for other java tools
      ln -s /opt/${pkgname}/JARS/$jar ${pkgdir}/usr/share/java/$jar
    done

    # Install Desktop File
    install -D -m644 $srcdir/${pkgname}.desktop \
        ${pkgdir}/usr/share/applications/${pkgname}.desktop

    # Install Icon File
    install -D -m644 $srcdir/icon.png \
        ${pkgdir}/usr/share/pixmaps/${pkgname}.png

    # Install Client Launcher
    install -D -m755 $srcdir/${pkgname}.launcher \
        ${pkgdir}/usr/bin/${pkgname}
}
# vim:set ts=2 sw=2 et:

