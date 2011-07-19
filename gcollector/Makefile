# All PHONY targets, here for convenience

PROGRAM = gcollect
DEBNAME = gcollector
DESTDIR = ''

prefix = usr
sbindir = $(prefix)/sbin
sysconfdir = etc

SUBDIRS = \
	./ \
	sbin/ \
	conf/ \
	conf/$(PROGRAM)/ \
	conf/$(PROGRAM)/ganglia.d/ \
	conf/$(PROGRAM)/ganglia.custom.d/ \

CLEANDIRS = \
	$(addsuffix *~,$(SUBDIRS)) \
	$(addsuffix *.bak,$(SUBDIRS)) \
	$(addsuffix *.tmp,$(SUBDIRS)) \
	$(addsuffix *.out,$(SUBDIRS))

.PHONY: install clean test sense
all: clean

install:
	@install -m 0600 -d $(DESTDIR)/$(sysconfdir)/$(PROGRAM)
	@install -m 0600 -d $(DESTDIR)/$(sysconfdir)/$(PROGRAM)/ganglia.d
	@install -m 0600 -d $(DESTDIR)/$(sysconfdir)/$(PROGRAM)/ganglia.custom.d
	@install -m 0640 conf/$(PROGRAM)/$(PROGRAM).cfg $(DESTDIR)/$(sysconfdir)/$(PROGRAM)/
	@install -m 0750 conf/$(PROGRAM)/ganglia.d/* $(DESTDIR)/$(sysconfdir)/$(PROGRAM)/ganglia.d/
	@install -m 0750 sbin/$(PROGRAM) $(DESTDIR)/$(sbindir)/
	@install -m 0750 sbin/niopid $(DESTDIR)/$(sbindir)/
clean:
	@rm -f $(CLEANDIRS)

deb:
	mkdir -pv $(CURDIR)/debian/$(DEBNAME)/$(sysconfdir)/$(PROGRAM)/
	mkdir -pv $(CURDIR)/debian/$(DEBNAME)/$(sysconfdir)/$(PROGRAM)/ganglia.d/
	mkdir -pv $(CURDIR)/debian/$(DEBNAME)/$(sysconfdir)/$(PROGRAM)/ganglia.custom.d/
	mkdir -pv $(CURDIR)/debian/$(DEBNAME)/$(sbindir)/
	debuild -uc -us -b

debclean:
	debuild clean
