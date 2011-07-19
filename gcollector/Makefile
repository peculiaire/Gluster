# All PHONY targets, here for convenience

PROGRAM = gcollect

prefix = /usr
sbindir = $(prefix)/sbin
sysconfdir = /etc

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
	@install -m 0600 -d $(sysconfdir)/$(PROGRAM)
	@install -m 0600 -d $(sysconfdir)/$(PROGRAM)/ganglia.d
	@install -m 0600 -d $(sysconfdir)/$(PROGRAM)/ganglia.custom.d
	@install -m 0640 conf/$(PROGRAM)/$(PROGRAM).cfg $(sysconfdir)/$(PROGRAM)/
	@install -m 0750 conf/$(PROGRAM)/ganglia.d/* $(sysconfdir)/$(PROGRAM)/ganglia.d/
	@install -m 0750 sbin/$(PROGRAM) $(sbindir)/

clean:
	@rm -f $(CLEANDIRS)
