VERSION=0.1
LANG1=san

BASENAME=apertium-$(LANG1)

TARGETS_COMMON = $(LANG1).automorf.bin $(LANG1).autogen.bin

###############################################################################
## Sanskrit transducer
###############################################################################

$(LANG1).automorf.bin: $(BASENAME).$(LANG1).dix
	apertium-validate-dictionary $(BASENAME).$(LANG1).dix
	lt-comp lr $(BASENAME).$(LANG1).dix $@

$(LANG1).autogen.bin: $(BASENAME).$(LANG1).dix
	apertium-validate-dictionary $(BASENAME).$(LANG1).dix
	lt-comp rl $(BASENAME).$(LANG1).dix $@

# This include defines goals for install-modes, .deps/.d and .mode files:
@ap_include@

###############################################################################
## Distribution
###############################################################################
EXTRA_DIST=$(BASENAME).$(LANG1).dix modes.xml

###############################################################################
## Installation stuff
###############################################################################
#
#   apertium_san_dir: This is where the compiled binaries go
#   apertium_san_srcdir: This is where the source files go

apertium_sandir=$(prefix)/share/apertium/apertium-$(PREFIX1)/
apertium_san_DATA=$(TARGETS_COMMON)

noinst_DATA=modes/$(LANG1)-morph.mode

install-data-local: install-modes
	$(INSTALL_DATA) $(BASENAME).$(LANG1).dix $(DESTDIR)$(apertium_san_srcdir)


###############################################################################
## Cleanup
###############################################################################


CLEANFILES = $(TARGETS_COMMON)
clean-local:
	-rm -rf .deps modes
