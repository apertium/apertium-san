VERSION=0.1
LANG1=san

BASENAME=apertium-$(LANG1)

TARGETS_COMMON = $(LANG1).automorf.bin 

TARGETS = $(TARGETS_COMMON) 

$(LANG1).automorf.bin: $(BASENAME).$(LANG1).dix
	apertium-validate-dictionary $(BASENAME).$(LANG1).dix
	lt-comp lr $(BASENAME).$(LANG1).dix $@


EXTRA_DIST=$(BASENAME).$(LANG1).dix modes.xml
           
apertium_sandir=$(prefix)/share/apertium/apertium-$(PREFIX1)/
apertium_san_DATA=$(PREFIX1).automorf.bin 
apertium_sanmodesdir=$(prefix)/share/apertium/modes/

CLEANFILES = $(TARGETS)

install-data-local:
	$(prefix)/bin/apertium-gen-modes modes.xml apertium-$(PREFIX1)
	test -d $(DESTDIR)$(apertium_sanmodesdir) || mkdir $(DESTDIR)$(apertium_sanmodesdir)
	$(INSTALL_DATA) $(PREFIX1)-morph.mode $(DESTDIR)$(apertium_sanmodesdir)
