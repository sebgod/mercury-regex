PCRE_VERSION   := 8.36
PCRE_NAME      := pcre-$(PCRE_VERSION)
PCRE_CFLAGS    := -Dregcomp=PCREregcomp
PCRE_OPTS      := --enable-jit --enable-unicode-properties
DOWNLOAD       := wget -N
UNPACK_TAR_BZ2 := tar jxf

.PHONY: all
all: $(PCRE_NAME)

$(PCRE_NAME):
	$(DOWNLOAD) -N http://sourceforge.net/projects/pcre/files/pcre/$(PCRE_VERSION)/$(PCRE_NAME).tar.bz2/download
	$(UNPACK_TAR_BZ2) download
	cd $(PCRE_NAME) && CFLAGS=$(PCRE_CFLAGS) ./configure $(PCRE_OPTS)>../$(PCRE_NAME).config.log && make >../$(PCRE_NAME).make.log

.PHONY: clean
clean:
	rm -fR pcre*


