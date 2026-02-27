# TP Lab 00 Report

## 1. Accounts
- Gmail: [georgij7305920@gmail.com]
- Telegram: [@KanishevGeorgij]
- GitHub: [georgij5920]

## 2. Development environment check
Output of version checks:

```bash
cmake --version
curl --version
git --version
g++ --version
make --version
tree --version
wget --version
openssl version

CMake suite maintained and supported by Kitware (kitware.com/cmake).
curl 8.14.1 (x86_64-pc-linux-gnu) libcurl/8.14.1 OpenSSL/3.5.4 zlib/1.3.1 brotli/1.1.0 zstd/1.5.7 libidn2/2.3.8 libpsl/0.21.2 libssh2/1.11.1 nghttp2/1.64.0 nghttp3/1.8.0 librtmp/2.3 OpenLDAP/2.6.10
Release-Date: 2025-06-04, security patched: 8.14.1-2+deb13u2
Protocols: dict file ftp ftps gopher gophers http https imap imaps ipfs ipns ldap ldaps mqtt pop3 pop3s rtmp rtsp scp sftp smb smbs smtp smtps telnet tftp ws wss
Features: alt-svc AsynchDNS brotli GSS-API HSTS HTTP2 HTTP3 HTTPS-proxy IDN IPv6 Kerberos Largefile libz NTLM PSL SPNEGO SSL threadsafe TLS-SRP UnixSockets zstd
git version 2.47.3
g++ (Debian 14.2.0-19) 14.2.0
Copyright (C) 2024 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

GNU Make 4.4.1
Built for x86_64-pc-linux-gnu
Copyright (C) 1988-2023 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
tree v2.2.1 © 1996 - 2024 by Steve Baker, Thomas Moore, Francesc Rocher, Florian Sesser, Kyosuke Tokoro
GNU Wget 1.25.0 built on linux-gnu.

-cares +digest -gpgme +https +ipv6 +iri +large-file -metalink +nls 
+ntlm +opie +psl +ssl/gnutls 

Wgetrc: 
    /etc/wgetrc (system)
Locale: 
    /usr/share/locale 
Compile: 
    gcc -DHAVE_CONFIG_H -DSYSTEM_WGETRC="/etc/wgetrc" 
    -DLOCALEDIR="/usr/share/locale" -I. -I../../src -I../lib 
    -I../../lib -Wdate-time -D_FORTIFY_SOURCE=2 
    -I/usr/include/p11-kit-1 -DHAVE_LIBGNUTLS -DNDEBUG -g -O2 
    -Werror=implicit-function-declaration 
    -ffile-prefix-map=/build/reproducible-path/wget-1.25.0=. 
    -fstack-protector-strong -fstack-clash-protection -Wformat 
    -Werror=format-security -fcf-protection -DNO_SSLv2 
Link: 
    gcc -I/usr/include/p11-kit-1 -DHAVE_LIBGNUTLS -DNDEBUG -g -O2 
    -Werror=implicit-function-declaration 
    -ffile-prefix-map=/build/reproducible-path/wget-1.25.0=. 
    -fstack-protector-strong -fstack-clash-protection -Wformat 
    -Werror=format-security -fcf-protection -DNO_SSLv2 -Wl,-z,relro 
    -Wl,-z,now -lpcre2-8 -luuid -lidn2 -lnettle -lgnutls -lz -lpsl 
    ../lib/libgnu.a 

Copyright (C) 2015 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later
<http://www.gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Originally written by Hrvoje Niksic <hniksic@xemacs.org>.
Please send bug reports and questions to <bug-wget@gnu.org>.
OpenSSL 3.5.4 30 Sep 2025 (Library: OpenSSL 3.5.4 30 Sep 2025)

Command for downloading utilities:

sudo apt install -y git g++ make cmake curl wget openssl

output:
git is already the newest version (1:2.47.3-0+deb13u1).
g++ is already the newest version (4:14.2.0-1).
make is already the newest version (4.4.1-2).
cmake is already the newest version (3.31.6-2).
curl is already the newest version (8.14.1-2+deb13u2).
wget is already the newest version (1.25.0-2).
openssl is already the newest version (3.5.4-1~deb13u2).
The following packages were automatically installed and are no longer required:
  libboost-program-options1.83.0   ruby-csv             ruby-rubygems
  libruby                          ruby-did-you-mean    ruby-sdbm
  libruby3.3                       ruby-net-telnet      ruby-webrick
  linux-image-6.12.43+deb13-amd64  ruby-optimist        ruby-xmlrpc
  rake                             ruby-paint           ruby3.3
  ruby                             ruby-ruby2-keywords  rubygems-integration
Use 'sudo apt autoremove' to remove them.

Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0

command for saving TOKEN:

umask 0077 && echo "MY_TOKEN" > ~/.gist
