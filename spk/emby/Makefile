SPK_NAME = emby
SPK_VERS = 4.4.3.0
SPK_REV = 11
SPK_ICON = src/emby.png
DSM_UI_DIR = app

BETA = 1

DEPENDS = cross/emby cross/busybox cross/sqlite

SPK_DEPENDS = "mono>5.8:ffmpeg>=2.6-3"

MAINTAINER = SynoCommunity

DESCRIPTION = Emby streams everything Your personal videos, music, photos, and live television in the palm of your hand.
ADMIN_PORT = 8096
RELOAD_UI = yes
DISPLAY_NAME = Emby
CHANGELOG = "Fix failing process stop."

HOMEPAGE = http://emby.media/
LICENSE  = GPL

INSTALLER_SCRIPT = src/installer.sh
SSS_SCRIPT       = src/dsm-control.sh
FWPORTS          = src/$(SPK_NAME).sc

INSTALL_PREFIX = /usr/local/$(SPK_NAME)

# Notify of unsupported architectures
UNSUPPORTED_ARCH = $(PPC_ARCHES)

POST_STRIP_TARGET = emby_extra_install

BUSYBOX_CONFIG = usrmng daemon
ENV += BUSYBOX_CONFIG="$(BUSYBOX_CONFIG)"

include ../../mk/spksrc.spk.mk

.PHONY: emby_extra_install
emby_extra_install:
	install -m 755 -d $(STAGING_DIR)/var
	install -m 755 -d $(STAGING_DIR)/app
	install -m 755 -d $(STAGING_DIR)/app/images
	for size in 16 24 32 48 72 ; \
	do \
	    convert $(SPK_ICON) -thumbnail $${size}x$${size} \
	            $(STAGING_DIR)/app/images/$(SPK_NAME)-$${size}.png ; \
	done
