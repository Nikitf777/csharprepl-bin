# Maintainer: Nikita Samusev nikitf777@gmail.com

pkgname=csharprepl-bin
provides=(csharprepl)
pkgver=0.6.7
pkgrel=1
pkgdesc="A command line C# REPL with syntax highlighting – explore the language, libraries and nuget packages interactively."
arch=('x86_64')
url="https://github.com/waf/CSharpRepl "
license=('MIT')
depends=('dotnet-runtime-8.0')
makedepends=('unzip')
source=("https://globalcdn.nuget.org/packages/csharprepl.0.6.7.nupkg?packageVersion=$pkgver")
sha256sums=('6b40a25370fa459a75145e39f4d21452bcb94c5443826e05461a8964d006616b')

package() {
    toolpath="tools/net8.0/any"

    # Install REPL files to /usr/lib/csharprepl
    mkdir -p "$pkgdir/usr/lib/csharprepl"
    cp -r "$srcdir/${toolpath}/." "$pkgdir/usr/lib/csharprepl/"

    # Create a wrapper script in /usr/bin
    bindir="$pkgdir/usr/bin"
    mkdir -p ${bindir}
    printf '#!/bin/sh\nexec dotnet exec /usr/lib/csharprepl/CSharpRepl.dll "$@"\n' > "${bindir}/csharprepl"
    chmod +x "${bindir}/csharprepl"
}
