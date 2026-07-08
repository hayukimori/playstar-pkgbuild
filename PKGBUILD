# Maintainer: Hayukimori
pkgname=playstar
pkgver=1.0.1
pkgrel=1
_tag=v1.0.1
pkgdesc="A personal music player built with Godot 4 and C#"
arch=('x86_64')
url="https://github.com/hayukimori/playstar"
license=('custom:BUSL-1.1')
depends=('vlc' 'gtk3')
options=('!strip')

source=("https://github.com/hayukimori/playstar/releases/download/$_tag/PlayStar-linux-x64.tar.gz")
sha256sums=('62b51a8e1c487df8614e8bb2f201e733884dd8cc10e98911a824d8a67adad3ac')

package() {
    cd "$srcdir"

    install -Dm755 "PlayStar" "$pkgdir/usr/share/playstar/PlayStar"
    cp -r "data_PlayStar_linuxbsd_x86_64" "$pkgdir/usr/share/playstar/"
    install -Dm644 "icon.png" "$pkgdir/usr/share/icons/hicolor/256x256/apps/playstar.png"
    install -Dm644 "playstar.desktop" "$pkgdir/usr/share/applications/playstar.desktop"

    install -Dm755 /dev/stdin "$pkgdir/usr/bin/playstar" <<'EOF'
#!/bin/sh
exec /usr/share/playstar/PlayStar "$@"
EOF

    install -Dm644 /dev/stdin "$pkgdir/usr/share/dbus-1/services/org.mpris.MediaPlayer2.playstar.service" <<'EOF'
[D-BUS Service]
Name=org.mpris.MediaPlayer2.playstar
Exec=/usr/bin/playstar
EOF
}
