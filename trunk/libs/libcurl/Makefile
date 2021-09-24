SRC_NAME=curl-7.7X.X

all: config_test
	$(MAKE) -j$(HOST_NCPU) -C $(SRC_NAME)

config_test:
	( if [ -f ./config_done ]; then \
		echo "the same configuration"; \
	else \
		make configure && touch config_done; \
	fi )

configure:
	( cd $(SRC_NAME) ; \
	./configure \
		--prefix=$(STAGEDIR) \
		--enable-static \
		--enable-openssl-auto-load-config \
		--disable-shared \
		$(if $(CONFIG_IPV6),--enable-ipv6,--disable-ipv6) \
		--disable-gopher \
		--disable-ldap \
		--disable-ldaps \
		--disable-rt \
		--disable-rtsp \
		--disable-telnet \
		--disable-tftp \
		--disable-smb \
		--disable-smtp \
		--disable-pop3 \
		--disable-imap \
		--disable-sspi \
		--disable-dict \
		--disable-ares \
		--disable-debug \
		--disable-curldebug \
		--disable-manual \
		--disable-verbose \
		--disable-tls-srp \
		--disable-libcurl-option \
		--disable-threaded-resolver \
		--without-brotli \
		--without-gnutls \
		--without-ca-path \
		--without-ca-fallback \
		--without-ca-bundle \
		--without-cyassl \
		--without-darwinssl \
		--without-default-ssl-backend \
		--without-libidn2 \
		--without-libmetalink \
		--without-libpsl \
		--without-librtmp \
		--without-libssh \
		--without-libssh2 \
		--without-krb4 \
		--without-nghttp2 \
		--without-nss \
		--without-mbedtls \
		--without-mesalink \
		--without-polarssl \
		--without-schannel \
		--without-wolfssl \
		--without-winidn \
		--without-winssl \
		--without-zsh-functions-dir \
		--with-random=/dev/urandom \
		--with-zlib=$(STAGEDIR) \
		--with-ssl=$(STAGEDIR) \
		--host=$(HOST_TARGET) \
		--build=$(HOST_BUILD) ; \
	)

clean:
	if [ -f $(SRC_NAME)/Makefile ] ; then \
		$(MAKE) -C $(SRC_NAME) clean ; \
		rm -r -f $(SRC_NAME)/lib/.deps ; \
		rm -r -f $(SRC_NAME)/src/.deps ; \
		rm -r -f $(SRC_NAME)/lib/vauth/.deps ; \
		rm -r -f $(SRC_NAME)/lib/vquic/.deps ; \
		rm -r -f $(SRC_NAME)/lib/vssh/.deps ; \
		rm -r -f $(SRC_NAME)/lib/vtls/.deps ; \
		rm -r -f $(SRC_NAME)/docs/examples/.deps ; \
		rm -r -f $(SRC_NAME)/tests/libtest/.deps ; \
		rm -r -f $(SRC_NAME)/tests/server/.deps ; \
		rm -r -f $(SRC_NAME)/tests/unit/.deps ; \
		rm -f $(SRC_NAME)/lib/Makefile ; \
		rm -f $(SRC_NAME)/lib/.dirstamp ; \
		rm -f $(SRC_NAME)/src/Makefile ; \
		rm -f $(SRC_NAME)/scripts/Makefile ; \
		rm -f $(SRC_NAME)/tests/Makefile ; \
		rm -f $(SRC_NAME)/tests/certs/scripts/Makefile ; \
		rm -f $(SRC_NAME)/tests/data/Makefile ; \
		rm -f $(SRC_NAME)/tests/libtest/Makefile ; \
		rm -f $(SRC_NAME)/tests/server/Makefile ; \
		rm -f $(SRC_NAME)/tests/unit/Makefile ; \
		rm -f $(SRC_NAME)/Makefile ; \
		rm -f $(SRC_NAME)/docs/cmdline-opts/Makefile ; \
		rm -f $(SRC_NAME)/docs/examples/Makefile ; \
		rm -f $(SRC_NAME)/docs/libcurl/Makefile ; \
		rm -f $(SRC_NAME)/docs/libcurl/opts/Makefile ; \
		rm -f $(SRC_NAME)/include/Makefile ; \
		rm -f $(SRC_NAME)/include/curl/Makefile ; \
		rm -f $(SRC_NAME)/packages/vms/Makefile ; \
		rm -f $(SRC_NAME)/packages/Makefile ; \
		rm -f $(SRC_NAME)/config.status ; \
		rm -f $(SRC_NAME)/config.cache ; \
		rm -f $(SRC_NAME)/config.log ; \
		rm -f $(SRC_NAME)/curl-config ; \
		rm -f $(SRC_NAME)/libcurl.pc ; \
		rm -f $(SRC_NAME)/libtool ; \
	fi ; \
	rm -f config_done

install:
	$(MAKE) -C $(SRC_NAME) install DESTDIR=""

romfs:

