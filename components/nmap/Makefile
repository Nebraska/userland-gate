
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

COMPONENT_NAME=         nmap
COMPONENT_VERSION=      5.51
COMPONENT_PROJECT_URL=	http://insecure.org/
COMPONENT_SRC=          $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tgz
COMPONENT_ARCHIVE_HASH= \
    sha256:d44cd28fc087a98056234ac56fc187b6742daa5c20f56bc4d524548042f4b25e
COMPONENT_ARCHIVE_URL=  http://nmap.org/dist/$(COMPONENT_ARCHIVE)

include ../../make-rules/prep.mk
include ../../make-rules/configure.mk
include ../../make-rules/ips.mk

COMPILER =	gcc

COMPONENT_PRE_CONFIGURE_ACTION = \
        ($(CLONEY) $(SOURCE_DIR) $(@D))

CONFIGURE_OPTIONS  +=   CFLAGS="$(CFLAGS)"
CONFIGURE_OPTIONS  +=   CXX="$(CXX)"
CONFIGURE_OPTIONS  +=   CXXFLAGS="$(CXXFLAGS)"
CONFIGURE_OPTIONS  +=   CPPFLAGS="$(CPPFLAGS)"
CONFIGURE_OPTIONS  +=   LIBS="-lsocket -lnsl"
CONFIGURE_OPTIONS  +=   PYTHON="$(PYTHON)"
CONFIGURE_OPTIONS  +=   --disable-shared 
CONFIGURE_OPTIONS  +=   --enable-static 
CONFIGURE_OPTIONS  +=   --disable-libtool-lock 
CONFIGURE_OPTIONS  +=   --localstatedir=/var 
CONFIGURE_OPTIONS  +=   --without-localdirs 
CONFIGURE_OPTIONS  +=   --with-zenmap 
CONFIGURE_OPTIONS  +=   --with-openssl
CONFIGURE_OPTIONS  +=   --with-libpcap
CONFIGURE_OPTIONS  +=   --with-libpcre
CONFIGURE_OPTIONS  +=   --with-liblua 
CONFIGURE_OPTIONS  +=   --with-ncat 
CONFIGURE_OPTIONS  +=   --with-ndiff
CONFIGURE_OPTIONS  +=   am_cv_python_pythondir=$(PYTHON_LIB)

# common targets
build:		$(BUILD_32)
		
install:	$(INSTALL_32) 

test:		$(NO_TESTS)

BUILD_PKG_DEPENDENCIES =	$(BUILD_TOOLS)

include ../../make-rules/depend.mk
