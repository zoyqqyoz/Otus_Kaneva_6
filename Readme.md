ДЗ 6. Управление пакетами. Дистрибьюция софта

1. Собираем Vagrantfile
2. Устанавливаем необходимые пакеты, предварительно исправив пути к репозиториям:
```
sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
yum install -y \
redhat-lsb-core \
wget \
rpmdevtools \
rpm-build \
createrepo \
yum-utils \
gcc

Upgraded:
  cups-libs-1:2.2.6-40.el8.x86_64         dnf-plugins-core-4.0.21-3.el8.noarch            elfutils-libelf-0.185-1.el8.x86_64 elfutils-libs-0.185-1.el8.x86_64 glibc-2.28-164.el8.x86_64           glibc-common-2.28-164.el8.x86_64
  glibc-langpack-en-2.28-164.el8.x86_64   ima-evm-utils-1.3.2-12.el8.x86_64               libblkid-2.32.1-28.el8.x86_64      libfdisk-2.32.1-28.el8.x86_64    libgcc-8.5.0-4.el8_5.x86_64         libgomp-8.5.0-4.el8_5.x86_64
  libmount-2.32.1-28.el8.x86_64           libsmartcols-2.32.1-28.el8.x86_64               libuuid-2.32.1-28.el8.x86_64       libxcrypt-4.1.1-6.el8.x86_64     ncurses-6.1-9.20180224.el8.x86_64   ncurses-base-6.1-9.20180224.el8.noarch
  ncurses-libs-6.1-9.20180224.el8.x86_64  python3-dnf-plugins-core-4.0.21-3.el8.noarch    python3-rpm-4.14.3-19.el8.x86_64   rpm-4.14.3-19.el8.x86_64         rpm-build-libs-4.14.3-19.el8.x86_64 rpm-libs-4.14.3-19.el8.x86_64
  rpm-plugin-selinux-4.14.3-19.el8.x86_64 rpm-plugin-systemd-inhibit-4.14.3-19.el8.x86_64 util-linux-2.32.1-28.el8.x86_64    yum-utils-4.0.21-3.el8.noarch

Installed:
  annobin-9.72-1.el8_5.2.x86_64                   at-3.1.20-11.el8.x86_64                                         bc-1.07.1-5.el8.x86_64                                      binutils-2.30-108.el8_5.1.x86_64
  cpp-8.5.0-4.el8_5.x86_64                        createrepo_c-0.17.2-3.el8.x86_64                                createrepo_c-libs-0.17.2-3.el8.x86_64                       cups-client-1:2.2.6-40.el8.x86_64
  drpm-0.4.1-3.el8.x86_64                         dwz-0.12-10.el8.x86_64                                          ed-1.14.2-4.el8.x86_64                                      efi-srpm-macros-3-3.el8.noarch
  elfutils-0.185-1.el8.x86_64                     emacs-filesystem-1:26.1-7.el8.noarch                            gc-7.6.4-3.el8.x86_64                                       gcc-8.5.0-4.el8_5.x86_64
  gdb-headless-8.2-16.el8.x86_64                  ghc-srpm-macros-1.4.2-7.el8.noarch                              glibc-devel-2.28-164.el8.x86_64                             glibc-headers-2.28-164.el8.x86_64
  go-srpm-macros-2-17.el8.noarch                  guile-5:2.0.14-7.el8.x86_64                                     isl-0.16.1-6.el8.x86_64                                     kernel-headers-4.18.0-348.7.1.el8_5.x86_64
  libatomic_ops-7.6.2-3.el8.x86_64                libbabeltrace-1.5.4-3.el8.x86_64                                libipt-1.6.1-8.el8.x86_64                                   libmpc-1.1.0-9.1.el8.x86_64
  libxcrypt-devel-4.1.1-6.el8.x86_64              m4-1.4.18-7.el8.x86_64                                          mailx-12.5-29.el8.x86_64                                    make-1:4.2.1-10.el8.x86_64
  ncurses-compat-libs-6.1-9.20180224.el8.x86_64   nspr-4.32.0-1.el8_4.x86_64                                      nss-3.67.0-7.el8_5.x86_64                                   nss-softokn-3.67.0-7.el8_5.x86_64
  nss-softokn-freebl-3.67.0-7.el8_5.x86_64        nss-sysinit-3.67.0-7.el8_5.x86_64                               nss-util-3.67.0-7.el8_5.x86_64                              ocaml-srpm-macros-5-4.el8.noarch
  openblas-srpm-macros-2-2.el8.noarch             patch-2.7.6-11.el8.x86_64                                       perl-Carp-1.42-396.el8.noarch                               perl-Data-Dumper-2.167-399.el8.x86_64
  perl-Digest-1.17-395.el8.noarch                 perl-Digest-MD5-2.55-396.el8.x86_64                             perl-Encode-4:2.97-3.el8.x86_64                             perl-Errno-1.28-420.el8.x86_64
  perl-Exporter-5.72-396.el8.noarch               perl-File-Path-2.15-2.el8.noarch                                perl-File-Temp-0.230.600-1.el8.noarch                       perl-Getopt-Long-1:2.50-4.el8.noarch
  perl-HTTP-Tiny-0.074-1.el8.noarch               perl-IO-1.38-420.el8.x86_64                                     perl-IO-Socket-IP-0.39-5.el8.noarch                         perl-IO-Socket-SSL-2.066-4.module_el8.3.0+410+ff426aa3.noarch
  perl-MIME-Base64-3.15-396.el8.x86_64            perl-Mozilla-CA-20160104-7.module_el8.3.0+416+dee7bcef.noarch   perl-Net-SSLeay-1.88-1.module_el8.3.0+410+ff426aa3.x86_64   perl-PathTools-3.74-1.el8.x86_64
  perl-Pod-Escapes-1:1.07-395.el8.noarch          perl-Pod-Perldoc-3.28-396.el8.noarch                            perl-Pod-Simple-1:3.35-395.el8.noarch                       perl-Pod-Usage-4:1.69-395.el8.noarch
  perl-Scalar-List-Utils-3:1.49-2.el8.x86_64      perl-Socket-4:2.027-3.el8.x86_64                                perl-Storable-1:3.11-3.el8.x86_64                           perl-Term-ANSIColor-4.06-396.el8.noarch
  perl-Term-Cap-1.17-395.el8.noarch               perl-Text-ParseWords-3.30-395.el8.noarch                        perl-Text-Tabs+Wrap-2013.0523-395.el8.noarch                perl-Time-Local-1:1.280-1.el8.noarch
  perl-URI-1.73-3.el8.noarch                      perl-Unicode-Normalize-1.25-396.el8.x86_64                      perl-constant-1.33-396.el8.noarch                           perl-interpreter-4:5.26.3-420.el8.x86_64
  perl-libnet-3.11-3.el8.noarch                   perl-libs-4:5.26.3-420.el8.x86_64                               perl-macros-4:5.26.3-420.el8.x86_64                         perl-parent-1:0.237-1.el8.noarch
  perl-podlators-4.11-1.el8.noarch                perl-srpm-macros-1-25.el8.noarch                                perl-threads-1:2.21-2.el8.x86_64                            perl-threads-shared-1.58-2.el8.x86_64
  postfix-2:3.5.8-2.el8.x86_64                    psmisc-23.1-5.el8.x86_64                                        python-rpm-macros-3-41.el8.noarch                           python-srpm-macros-3-41.el8.noarch
  python3-rpm-macros-3-41.el8.noarch              qt5-srpm-macros-5.15.2-1.el8.noarch                             redhat-lsb-core-4.1-47.el8.x86_64                           redhat-lsb-submod-security-4.1-47.el8.x86_64
  redhat-rpm-config-125-1.el8.noarch              rpm-build-4.14.3-19.el8.x86_64                                  rpmdevtools-8.10-8.el8.noarch                               rust-srpm-macros-5-2.el8.noarch
  spax-1.5.3-13.el8.x86_64                        time-1.9-3.el8.x86_64                                           tpm2-tss-2.3.2-4.el8.x86_64                                 unzip-6.0-45.el8_4.x86_64
  util-linux-user-2.32.1-28.el8.x86_64            wget-1.19.5-10.el8.x86_64                                       zip-3.0-23.el8.x86_64                                       zstd-1.4.4-1.el8.x86_64


```

3. Скачаем пакет nginx и устанавливаем его
```
wget https://nginx.org/packages/centos/8/SRPMS/nginx-1.20.2-1.el8.ngx.src.rpm
rpm -i nginx-1.*

[root@otusrpm ~]# ls -l rpmbuild/
total 0
drwxr-xr-x. 2 root root 246 May 25 13:52 SOURCES
drwxr-xr-x. 2 root root  24 May 25 13:52 SPECS

```

4. Скачиваем и распаковываем openssl
```
wget https://github.com/openssl/openssl/archive/refs/heads/OpenSSL_1_1_1-stable.zip
unzip OpenSSL_1_1_1-stable.zip
```

5. Заранее установим все зависимости для nginx
```
yum-builddep rpmbuild/SPECS/nginx.spec

Upgraded:
  e2fsprogs-1.45.6-2.el8.x86_64      e2fsprogs-libs-1.45.6-2.el8.x86_64       keyutils-1.5.10-9.el8.x86_64       keyutils-libs-1.5.10-9.el8.x86_64       krb5-libs-1.18.2-14.el8.x86_64         libcom_err-1.45.6-2.el8.x86_64
  libselinux-2.9-5.el8.x86_64        libselinux-utils-2.9-5.el8.x86_64        libsepol-2.9-3.el8.x86_64          libss-1.45.6-2.el8.x86_64               openssl-1:1.1.1k-5.el8_5.x86_64        openssl-libs-1:1.1.1k-5.el8_5.x86_64
  pcre-8.42-6.el8.x86_64             python3-libselinux-2.9-5.el8.x86_64      systemd-239-51.el8_5.2.x86_64      systemd-libs-239-51.el8_5.2.x86_64      systemd-pam-239-51.el8_5.2.x86_64      systemd-udev-239-51.el8_5.2.x86_64
  zlib-1.2.11-17.el8.x86_64

Installed:
  keyutils-libs-devel-1.5.10-9.el8.x86_64    krb5-devel-1.18.2-14.el8.x86_64          libcom_err-devel-1.45.6-2.el8.x86_64    libkadm5-1.18.2-14.el8.x86_64      libselinux-devel-2.9-5.el8.x86_64    libsepol-devel-2.9-3.el8.x86_64
  libverto-devel-0.3.0-5.el8.x86_64          openssl-devel-1:1.1.1k-5.el8_5.x86_64    pcre-cpp-8.42-6.el8.x86_64              pcre-devel-8.42-6.el8.x86_64       pcre-utf16-8.42-6.el8.x86_64         pcre-utf32-8.42-6.el8.x86_64
  pcre2-devel-10.32-2.el8.x86_64             pcre2-utf16-10.32-2.el8.x86_64           pcre2-utf32-10.32-2.el8.x86_64          zlib-devel-1.2.11-17.el8.x86_64

```

6. Отредактируем файл nginx.spec, добавив в него информацию о openssl 
```
%build
./configure %{BASE_CONFIGURE_ARGS} \
    --with-cc-opt="%{WITH_CC_OPT}" \
    --with-ld-opt="%{WITH_LD_OPT}" \
    --with-openssl=/root/openssl-OpenSSL_1_1_1-stable
    --with-debug
```

7. Приступим к сборке пакета
```
rpmbuild -bb rpmbuild/SPECS/nginx.spec

Executing(%clean): /bin/sh -e /var/tmp/rpm-tmp.7S49d6
+ umask 022
+ cd /root/rpmbuild/BUILD
+ cd nginx-1.20.2
+ /usr/bin/rm -rf /root/rpmbuild/BUILDROOT/nginx-1.20.2-1.el8.ngx.x86_64
+ exit 0
```

8. Убедимся, что пакеты создались
```
[root@otusrpm ~]# ls rpmbuild/RPMS/x86_64/
nginx-1.20.2-1.el8.ngx.x86_64.rpm  nginx-debuginfo-1.20.2-1.el8.ngx.x86_64.rpm
```

9. Установим nginx и проверим работоспособность
```
yum localinstall -y rpmbuild/RPMS/x86_64/nginx-1.20.2-1.el8.ngx.x86_64.rpm
Failed to set locale, defaulting to C.UTF-8
Last metadata expiration check: 0:25:29 ago on Thu May 25 13:48:42 2023.
Dependencies resolved.
=============================================================================================================================================================================================================================================
 Package                                             Architecture                                         Version                                                           Repository                                                  Size
=============================================================================================================================================================================================================================================
Installing:
 nginx                                               x86_64                                               1:1.20.2-1.el8.ngx                                                @commandline                                               2.1 M

Transaction Summary
=============================================================================================================================================================================================================================================
Install  1 Package

Total size: 2.1 M
Installed size: 6.1 M
Downloading Packages:
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                                                                                                                     1/1
  Running scriptlet: nginx-1:1.20.2-1.el8.ngx.x86_64                                                                                                                                                                                     1/1
  Installing       : nginx-1:1.20.2-1.el8.ngx.x86_64                                                                                                                                                                                     1/1
  Running scriptlet: nginx-1:1.20.2-1.el8.ngx.x86_64                                                                                                                                                                                     1/1
----------------------------------------------------------------------

Thanks for using nginx!

Please find the official documentation for nginx here:
* https://nginx.org/en/docs/

Please subscribe to nginx-announce mailing list to get
the most important news about nginx:
* https://nginx.org/en/support.html

Commercial subscriptions for nginx are available on:
* https://nginx.com/products/

----------------------------------------------------------------------

  Verifying        : nginx-1:1.20.2-1.el8.ngx.x86_64                                                                                                                                                                                     1/1

Installed:
  nginx-1:1.20.2-1.el8.ngx.x86_64

Complete!
[root@otusrpm ~]# systemctl start nginx
[root@otusrpm ~]# systemctl status nginx
● nginx.service - nginx - high performance web server
   Loaded: loaded (/usr/lib/systemd/system/nginx.service; disabled; vendor preset: disabled)
   Active: active (running) since Thu 2023-05-25 14:15:41 UTC; 19s ago
     Docs: http://nginx.org/en/docs/
  Process: 50074 ExecStart=/usr/sbin/nginx -c /etc/nginx/nginx.conf (code=exited, status=0/SUCCESS)
 Main PID: 50075 (nginx)
    Tasks: 3 (limit: 12421)
   Memory: 3.1M
   CGroup: /system.slice/nginx.service
           ├─50075 nginx: master process /usr/sbin/nginx -c /etc/nginx/nginx.conf
           ├─50076 nginx: worker process
           └─50077 nginx: worker process

May 25 14:15:41 otusrpm systemd[1]: Starting nginx - high performance web server...
May 25 14:15:41 otusrpm systemd[1]: Started nginx - high performance web server.
```

10. Создадим директорию для собственного репозитория и скопируем туда наш собранный RPM и RPM для установки репозитория Percona-Server
```
mkdir /usr/share/nginx/html/repo
cp rpmbuild/RPMS/x86_64/nginx-1.20.2-1.el8.ngx.x86_64.rpm /usr/share/nginx/html/repo/
wget https://downloads.percona.com/downloads/percona-distribution-mysql-ps/percona-distribution-mysql-ps-8.0.32/binary/redhat/8/x86_64/percona-orchestrator-3.2.6-8.el8.x86_64.rpm -O /usr/share/nginx/html/repo/percona-orchestrator-3.2.6-2.el8.x86_64.rpm
```

11. Инициализируем репозиторий командой
```
[root@otusrpm ~]# createrepo /usr/share/nginx/html/repo/
Directory walk started
Directory walk done - 2 packages
Temporary output repo path: /usr/share/nginx/html/repo/.repodata/
Preparing sqlite DBs
Pool started (with 5 workers)
Pool finished
```

12. Настроим в NGINX доступ к листингу каталога
```
nano /etc/nginx/conf.d/default.conf
location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
        autoindex on;
    }
```

13. Проверяем синтаксис и перезапускаем NGINX
```
[root@otusrpm ~]# nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

[root@otusrpm ~]# nginx -s reload
```

14. Проверяем репозиторий
```
[root@otusrpm ~]# curl -a http://localhost/repo/
<html>
<head><title>Index of /repo/</title></head>
<body>
<h1>Index of /repo/</h1><hr><pre><a href="../">../</a>
<a href="repodata/">repodata/</a>                                          25-May-2023 14:56                   -
<a href="nginx-1.20.2-1.el8.ngx.x86_64.rpm">nginx-1.20.2-1.el8.ngx.x86_64.rpm</a>                  25-May-2023 14:36             2250360
<a href="percona-orchestrator-3.2.6-2.el8.x86_64.rpm">percona-orchestrator-3.2.6-2.el8.x86_64.rpm</a>        15-Mar-2023 17:38             5214524
</pre><hr></body>
</html>
```

15. Добавляем его в /etc/yum.repos.d
```
cat >> /etc/yum.repos.d/otus.repo << EOF
[otus]
name=otus-linux
baseurl=http://localhost/repo
gpgcheck=0
enabled=1
EOF
```

16. Убедимся, что репозиторий подключился, проверяем, что в нём
```
[root@otusrpm ~]# yum repolist enabled | grep otus
Failed to set locale, defaulting to C.UTF-8
otus                            otus-linux

[root@otusrpm ~]# yum list | grep otus
Failed to set locale, defaulting to C.UTF-8
otus-linux                                      789 kB/s | 2.8 kB     00:00
percona-orchestrator.x86_64                            2:3.2.6-8.el8                                          otus
```

17. Установим репозиторий percona-release
```
[root@otusrpm ~]# yum install percona-orchestrator.x86_64 -y
Failed to set locale, defaulting to C.UTF-8
Last metadata expiration check: 0:01:58 ago on Mon May 29 06:46:35 2023.
Dependencies resolved.
=============================================================================================================================================================================================================================================
 Package                                                          Architecture                                       Version                                                     Repository                                             Size
=============================================================================================================================================================================================================================================
Installing:
 percona-orchestrator                                             x86_64                                             2:3.2.6-8.el8                                               otus                                                  5.0 M
Installing dependencies:
 jq                                                               x86_64                                             1.5-12.el8                                                  appstream                                             161 k
 oniguruma                                                        x86_64                                             6.8.2-2.el8                                                 appstream                                             187 k

Transaction Summary
=============================================================================================================================================================================================================================================
Install  3 Packages

Total download size: 5.3 M
Installed size: 17 M
Downloading Packages:
(1/3): percona-orchestrator-3.2.6-2.el8.x86_64.rpm                                                                                                                                                            99 MB/s | 5.0 MB     00:00
(2/3): jq-1.5-12.el8.x86_64.rpm                                                                                                                                                                              296 kB/s | 161 kB     00:00
(3/3): oniguruma-6.8.2-2.el8.x86_64.rpm                                                                                                                                                                      327 kB/s | 187 kB     00:00
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                                                        9.2 MB/s | 5.3 MB     00:00
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                                                                                                                     1/1
  Installing       : oniguruma-6.8.2-2.el8.x86_64                                                                                                                                                                                        1/3
  Running scriptlet: oniguruma-6.8.2-2.el8.x86_64                                                                                                                                                                                        1/3
  Installing       : jq-1.5-12.el8.x86_64                                                                                                                                                                                                2/3
  Installing       : percona-orchestrator-2:3.2.6-8.el8.x86_64                                                                                                                                                                           3/3
  Running scriptlet: percona-orchestrator-2:3.2.6-8.el8.x86_64                                                                                                                                                                           3/3
  Verifying        : jq-1.5-12.el8.x86_64                                                                                                                                                                                                1/3
  Verifying        : oniguruma-6.8.2-2.el8.x86_64                                                                                                                                                                                        2/3
  Verifying        : percona-orchestrator-2:3.2.6-8.el8.x86_64                                                                                                                                                                           3/3

Installed:
  jq-1.5-12.el8.x86_64                                                 oniguruma-6.8.2-2.el8.x86_64                                                 percona-orchestrator-2:3.2.6-8.el8.x86_64

Complete!
```









