# Maintainer: nkn <rstancuna at gmail dot com>
pkgname=tvmaxe-cli-git
pkgver=20140814
pkgrel=1
pkgdesc="tv-maxe in cli"
arch=('any')
url=https://github.com/calvarr/tvmaxe-cli
license=('GPL')
depends=('dialog' 'sed' 'awk' 'wget' 'rtmpdump' 'livestreamer' 'youtube-dl' 'sopcast' 'ffmpeg' 'dialog' 'mplayer' 'axel')
makedepends=('git')
optdepends=("vlc: alternative player"
            "omxplayer: alternative player for raspberry pi")
replaces=('tvmaxe-cli')
conflicts=('tvmaxe-cli')

_gitroot="https://github.com/calvarr/tvmaxe-cli.git"
_gitname="tvmaxe-cli"

package() {
  cd "$srcdir"
  msg "Connecting to Git server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "Git checkout done or server timeout"
  msg "Starting build..."
  
  cd "$srcdir/$_gitname"
  install -Dm755 tvmaxe-cli "$pkgdir/usr/bin/tvmaxe-cli"
  install -d "$pkgdir/home/$USER/.tvmaxe-cli"
  cp -apr ./* "$pkgdir/home/$USER/.tvmaxe-cli/" 
  chown -R $USER:users "$pkgdir/home/$USER/.tvmaxe-cli/"
}

# vim:set ts=2 sw=2 et:
