#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL"), version 1.0.
# You may only use this file in accordance with the terms of version
# 1.0 of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source.  A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2022 Niklas Poslovski
#

BUILD_BITS= 64
BUILD_STYLE=	meson

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=         gst-rtsp-server1
COMPONENT_VERSION=      1.20.3
COMPONENT_SUMMARY=      Multimedia graph framework - rtsp server
COMPONENT_SRC_NAME=	gst-rtsp-server
COMPONENT_SRC=          $(COMPONENT_SRC_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH= sha256:ee402718be9b127f0e5e66ca4c1b4f42e4926ec93ba307b7ccca5dc6cc9794ca
COMPONENT_PROJECT_URL=	https://gstreamer.freedesktop.org/
COMPONENT_ARCHIVE_URL=	$(COMPONENT_PROJECT_URL)/src/$(COMPONENT_SRC_NAME)/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=         library/audio/gstreamer1/rtsp-server
COMPONENT_CLASSIFICATION=	System/Multimedia Libraries
COMPONENT_LICENSE=      LGPLv2
COMPONENT_LICENSE_FILE= gst-rtsp-server1.license

include $(WS_MAKE_RULES)/encumbered.mk
include $(WS_MAKE_RULES)/common.mk

#gcc_OPT = -O2

PATH = $(PATH.gnu)

# gobject-introspection
COMPONENT_BUILD_ENV += CC="$(CC)"
COMPONENT_BUILD_ENV += CFLAGS="$(CFLAGS)"

unexport SHELLOPTS

COMPONENT_TEST_TRANSFORMS += \
	'-e "s/[0-9]*\.[0-9]*s//" ' \
    '-n ' \
    '-e "/Summary/p" ' \
    '-e "/TIMEOUT/p" ' \
    '-e "/Ok/p" ' \
    '-e "/Fail/p" ' \
    '-e "/Pass/p" ' \
    '-e "/Skipped/p" ' \
    '-e "/Timeout/p" '
# build dependency not detected by REQUIRED_PACKAGES
REQUIRED_PACKAGES += system/header/header-audio

# Manually added dependencies
REQUIRED_PACKAGES += library/audio/gstreamer1/plugin/bad

# Auto-generated dependencies
REQUIRED_PACKAGES += library/audio/gstreamer1
REQUIRED_PACKAGES += library/audio/gstreamer1/plugin/base
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += system/library
