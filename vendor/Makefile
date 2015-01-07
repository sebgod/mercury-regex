DOWNLOAD       := wget -N
UNPACK_TAR_BZ2 := tar jxf
UNPACK_7Z      := 7za x -bd -y -scsUTF-8
MKDIR          := mkdir -p
DEL_DIR        := rm -fR

PCRE_VERSION   := 8.36
PCRE_BASE_URL  := http://sourceforge.net/projects/pcre/files/pcre
PCRE_NAME      := pcre-$(PCRE_VERSION)
PCRE_CFLAGS    := -Dregcomp=PCREregcomp
PCRE_OPTS      := --enable-jit --enable-unicode-properties

XZ_VERSION  := 5.2.0
XZ_BASE_URL := http://tukaani.org/xz
XZ_NAME     := xz-$(XZ_VERSION)

.PHONY: all
all: $(PCRE_NAME)

$(PCRE_NAME):
	$(DOWNLOAD) $(PCRE_BASE_URL)/$(PCRE_VERSION)/$@.tar.bz2/download
	( $(UNPACK_TAR_BZ2) download || $(UNPACK_TAR_BZ2) $@.tar.bz2 )
	cd $@ && CFLAGS=$(PCRE_CFLAGS) ./configure $(PCRE_OPTS)>../$@.config.log && make >../$@.make.log

$(XZ_NAME):
	$(DOWNLOAD) $(XZ_BASE_URL)/$@-windows.7z
	$(UNPACK_7Z) -o$@ $@-windows.7z

.PHONY: clean
clean:
	$(DEL_DIR) pcre-*
	$(DEL_DIR) xz-*


