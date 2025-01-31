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
# Copyright 2021 Gary Mills
# Copyright 2021, 2022 Andreas Wacknitz
#

BUILD_STYLE= setup.py
BUILD_BITS= NO_ARCH
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		astroid
COMPONENT_VERSION=	2.9.3
COMPONENT_SUMMARY=	A common base representation of python source code
COMPONENT_PROJECT_URL=	https://github.com/PyCQA/astroid
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH= sha256:07234423c3722df6aa067c15f5fa60adf4f1d6ae659d2ab147acb40a8a1904f7
# Downloading the package source from pypi misses the tests, thus we a download from Github:
COMPONENT_ARCHIVE_URL=	$(COMPONENT_PROJECT_URL)/archive/refs/tags/v$(COMPONENT_VERSION).tar.gz
COMPONENT_FMRI=		library/python/astroid
COMPONENT_CLASSIFICATION=	Development/Python
COMPONENT_LICENSE=	LGPLv2.1, GPLv2

# Set python version used by this product
PYTHON_VERSION=		3.9
PYTHON_VERSIONS=	3.9

include $(WS_MAKE_RULES)/common.mk

# Tests fail because numpy cannot be compiled.
COMPONENT_TEST_DIR = $(COMPONENT_SRC)/tests
COMPONENT_TEST_CMD = tox -e py39
COMPONENT_TEST_ARGS =
COMPONENT_TEST_MASTER = $(COMPONENT_TEST_RESULTS_DIR)/results-all.master
COMPONENT_TEST_TRANSFORMS += \
	'-e "s/in [0-9]*\.[0-9]*s //"' \
	'-n' \
	'-e "/===/p"' \
	'-e "/collected/p"' \
	'-e "/^FAILED/p"' \
	'-e "/^E /p"' \
	'-e "/^\.\.\./p"' \
	'-e "/^unittest_/p"'

# Manually added test dependencies:
REQUIRED_PACKAGES += library/python/flaky-39
REQUIRED_PACKAGES += library/python/hypothesis-39
REQUIRED_PACKAGES += library/python/lazy_object_proxy-39
REQUIRED_PACKAGES += library/python/pluggy-39
REQUIRED_PACKAGES += library/python/py-39
REQUIRED_PACKAGES += library/python/pytest-39
REQUIRED_PACKAGES += library/python/pytest-benchmark-39
REQUIRED_PACKAGES += library/python/pytest-reporter-39
REQUIRED_PACKAGES += library/python/setuptools-39
REQUIRED_PACKAGES += library/python/typing_extensions-39
REQUIRED_PACKAGES += library/python/wrapt-39
REQUIRED_PACKAGES += library/python/tox

# Auto-generated dependencies
REQUIRED_PACKAGES += runtime/python-39
