# Maintainer: Hayukimori
pkgname=playstar
pkgver=1.2.4
pkgrel=1
_tag=v1.2.4
pkgdesc="A personal music player built with Godot 4 and C#"
arch=('x86_64')
url="https://github.com/hayukimori/playstar"
license=('custom:BUSL-1.1')
depends=('vlc' 'gtk3')
options=('!strip')

source=("https://github.com/hayukimori/playstar/releases/download/$_tag/PlayStar-linux-x64.tar.gz")
sha256sums=('c4e8c82273e70e24fc88a4c725177525525fe0eb8de3fd15d8a00b04215c6268')

package() {
    cd "$srcdir"

    install -Dm755 "PlayStar" "$pkgdir/usr/share/playstar/PlayStar"
    install -Dm755 "playstar-runner" "$pkgdir/usr/share/playstar/playstar-runner"
    cp -r "data_PlayStar_linuxbsd_x86_64" "$pkgdir/usr/share/playstar/"
    install -Dm644 "icon.png" "$pkgdir/usr/share/icons/hicolor/256x256/apps/playstar.png"
    install -Dm644 "playstar.desktop" "$pkgdir/usr/share/applications/playstar.desktop"

    install -Dm755 /dev/stdin "$pkgdir/usr/bin/playstar" <<'EOF'
#!/bin/sh
exec /usr/share/playstar/playstar-runner "$@"
EOF

    install -Dm644 /dev/stdin "$pkgdir/usr/share/dbus-1/services/org.mpris.MediaPlayer2.playstar.service" <<'EOF'
[D-BUS Service]
Name=org.mpris.MediaPlayer2.playstar
Exec=/usr/bin/playstar
EOF
}
