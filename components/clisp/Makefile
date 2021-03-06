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
# Copyright (c) 2011, 2012, Oracle and/or its affiliates. All rights reserved.
#

include ../../make-rules/shared-macros.mk

COMPONENT_NAME=		clisp
COMPONENT_VERSION=	2.49
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_PROJECT_URL=	http://clisp.cons.org/
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH=	\
    sha256:8132ff353afaa70e6b19367a25ae3d5a43627279c25647c220641fed00f8e890
COMPONENT_ARCHIVE_URL=	http://ftp.gnu.org/gnu/clisp/release/$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)

include ../../make-rules/prep.mk
include ../../make-rules/configure.mk
include ../../make-rules/ips.mk

# To include correct locale header file in .../modules/regexp/gllib/regex.c
CPPFLAGS += -I/usr/share/gettext/intl

# Required to configure correctly.
COMPONENT_PRE_CONFIGURE_ACTION = \
	($(CLONEY) $(SOURCE_DIR) $(@D))

COMPILER=	gcc
PATCH_LEVEL=	0

# SHELLOPTS appears to cause clisp's configure script to fail while
# checking the compiler.
unexport SHELLOPTS

# clisp's configure script is not a GNU auto* tools generated configure script
# and doesn't take --sbindir, so we need to override the default values.
CONFIGURE_OPTIONS = CC="$(CC) -DNO_GENERATIONAL_GC"
CONFIGURE_OPTIONS += CPPFLAGS="$(CPPFLAGS)"
CONFIGURE_OPTIONS += --prefix=$(CONFIGURE_PREFIX)
CONFIGURE_OPTIONS += --mandir=$(CONFIGURE_MANDIR)
CONFIGURE_OPTIONS += --bindir=$(CONFIGURE_BINDIR.$(BITS))
CONFIGURE_OPTIONS += --libdir=$(CONFIGURE_LIBDIR.$(BITS))
CONFIGURE_OPTIONS += --srcdir=$(SOURCE_DIR)
CONFIGURE_OPTIONS += --with-libsigsegv-prefix=$(CONFIGURE_PREFIX)
CONFIGURE_OPTIONS += --with-libreadline-prefix=$(CONFIGURE_PREFIX)

# One of the tests now needs the GNU tail command.
COMPONENT_TEST_ENV +=  PATH="$(GNUBIN):$(PATH)"

# common targets
build:		$(BUILD_32)

install:	$(INSTALL_32)

test:		$(TEST_32)

BUILD_PKG_DEPENDENCIES =	$(BUILD_TOOLS)

include ../../make-rules/depend.mk
