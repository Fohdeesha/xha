#
#   scripts/Makefile
#

TARGET_DIR=scripts
DEFMAKE=default-debug.mk
include ../$(DEFMAKE)

TARGET          = ha_errnorc

TARGET_GENERR   = ./generr
OBJS_GENERR     += generr.o

all: $(TARGET)

$(TARGET): $(TARGET_GENERR)
	$(TARGET_GENERR) > $@
	@chmod 0755 $@

$(TARGET_GENERR): $(OBJS_GENERR) $(HALIBS)
	$(CC) $(OBJS_GENERR) $(HALIBS) $(LIBS) -o $@
	@chmod 0755 $@

$(HALIBS):

install: $(TARGET)
	@mkdir -p $(DESTDIR)$(INSDIR)
	@cp ha_* $(DESTDIR)$(INSDIR)
	@mkdir -p $(DESTDIR)$(LOGCONFDIR)
	@cp logrotate.xha.conf $(DESTDIR)$(LOGCONFDIR)/xha
	@chmod 0644 $(DESTDIR)$(LOGCONFDIR)/xha
	@mkdir -p $(DESTDIR)/etc/portreserve
	@cp etc_portreserve_xhad $(DESTDIR)/etc/portreserve/xhad

clean:
	rm -f $(TARGET) $(TARGET_GENERR) $(OBJS_GENERR)
