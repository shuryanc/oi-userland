#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

#
# Copyright (c) 2010, 2016, Oracle and/or its affiliates. All rights reserved.
# Copyright (c) 2019, Michal Nowak
# Copyright (c) 2022, Andreas Wacknitz
#

BUILD_BITS=		64_and_32
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		gnutls
COMPONENT_MJR_VERSION=	3.6
COMPONENT_VERSION=	$(COMPONENT_MJR_VERSION).16
COMPONENT_REVISION=	1
COMPONENT_PROJECT_URL=  https://gnutls.org/
COMPONENT_SUMMARY=	GNU transport layer security library
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH= sha256:1b79b381ac283d8b054368b335c408fedcb9b7144e0c07f531e3537d4328f3b3
COMPONENT_ARCHIVE_URL=  https://www.gnupg.org/ftp/gcrypt/gnutls/v$(COMPONENT_MJR_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_SIG_URL=	$(COMPONENT_ARCHIVE_URL).sig
COMPONENT_FMRI=		library/gnutls-3
COMPONENT_CLASSIFICATION=	System/Libraries
COMPONENT_LICENSE=	GPLv3, LGPLv2.1, FDLv1.3

include $(WS_MAKE_RULES)/common.mk

CFLAGS += -I$(USRINCDIR)/idn2

CONFIGURE_OPTIONS += --disable-guile
CONFIGURE_OPTIONS += --disable-dependency-tracking

unexport SHELLOPTS

#COMPONENT_TEST_MASTER = $(COMPONENT_TEST_RESULTS_DIR)/results-all.master

COMPONENT_TEST_TRANSFORMS += \
	'-n -e "/SKIP/p" ' \
	'-e "/PASS/p" ' \
	'-e "/FAIL/p" ' \
	'-e "/TOTAL/p" ' \
	'-e "/ERROR/p" '

# Auto-generated dependencies
REQUIRED_PACKAGES += $(GCC_RUNTIME_PKG)
REQUIRED_PACKAGES += $(GXX_RUNTIME_PKG)
REQUIRED_PACKAGES += developer/build/autogen
REQUIRED_PACKAGES += library/desktop/p11-kit
REQUIRED_PACKAGES += library/gmp
REQUIRED_PACKAGES += library/libidn2
REQUIRED_PACKAGES += library/libtasn1
REQUIRED_PACKAGES += library/libunistring
REQUIRED_PACKAGES += library/nettle
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
