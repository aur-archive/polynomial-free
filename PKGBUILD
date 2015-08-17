# Maintainer: kfgz <kfgz at interia pl>

pkgname=polynomial-free
pkgver=135
pkgrel=1
arch=('i686' 'x86_64')
pkgdesc="A 3D space shooter with mathematically generated fractal scenery and models"
url="http://dmytry.pandromeda.com/games/try_polynomial.html"
license=('unknown')
depends=('alure' 'fontconfig' 'gstreamer0.10-base' 'libpng' 'libvorbis' 'mesa' 'pango')
source=(http://dmytry.com/games/Polynomial-free-${pkgver}_linux.tar.gz
        ${pkgname}
        ${pkgname}.desktop
        ${pkgname}.png)
noextract=(Polynomial-free-${pkgver}_linux.tar.gz)
#md5sums=('2af4d4dae8e19e87a1dc9c7031155080'
md5sums=('2895afa6cc68e2e1ee09d6d39c5757c0'
         'e7d3d3485b4c5dfc1fed5a8f1f4d63a7'
         '8524e8d019c2644968529cdbeaf55351'
         '55829b1b75a167637fed5495335c53af')

package() {
  install -dm755 "${pkgdir}"/opt/${pkgname}
  
  gzip -d "${startdir}"/Polynomial-free-${pkgver}_linux.tar.gz
  tar -xvf ${startdir}/Polynomial-free-135_linux.tar -C "${srcdir}"
    
  cd "${srcdir}"/Polynomial-free-${pkgver}_linux
  mv * "${pkgdir}"/opt/${pkgname}
    
  if [ `uname -m` = "x86_64" ]; then
    rm "${pkgdir}"/opt/${pkgname}/bin/Polynomial32
    rm "${pkgdir}"/opt/polynomial-free/Polynomial32
    rm -r "${pkgdir}"/opt/${pkgname}/bin/lib32

  else
    rm "${pkgdir}"/opt/${pkgname}/bin/Polynomial64
    rm "${pkgdir}"/opt/polynomial-free/Polynomial64
    rm -r "${pkgdir}"/opt/${pkgname}/bin/lib64    
  fi
  
  install -dm755 "${pkgdir}"/usr/{bin,share/{applications,pixmaps}}
  
  cd "${srcdir}"
  install -m755 ${pkgname} "${pkgdir}"/usr/bin
  install -m644 ${pkgname}.desktop "${pkgdir}"/usr/share/applications
  install -m644 ${pkgname}.png "${pkgdir}"/usr/share/pixmaps
}
