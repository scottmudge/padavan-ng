SRC_NAME=jpeg-9X

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
	libtoolize --force ; \
	aclocal ; \
	autoheader ; \
	automake --force-missing --add-missing ; \
	autoconf ; \
	./configure \
		--prefix=$(STAGEDIR) \
		--enable-static \
		--disable-shared \
		--host=$(HOST_TARGET) \
		--build=$(HOST_BUILD) ; \
	)

clean:
	if [ -f $(SRC_NAME)/Makefile ] ; then \
		$(MAKE) -C $(SRC_NAME) distclean ; \
	fi ; \
	rm -f config_done

install:
	$(MAKE) -C $(SRC_NAME) install DESTDIR=""

romfs:

