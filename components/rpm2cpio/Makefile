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
# Copyright (c) 2011, Oracle and/or its affiliates. All rights reserved.
#

include ../../make-rules/shared-macros.mk

# The version of rpm2cpio.pl delivered in SFW does not seem to be
# available for download anymore, so it is exceptionally delivered in
# the Userland gate itself.
#
COMPONENT_NAME=		rpm2cpio
COMPONENT_VERSION=	0.5.11
COMPONENT_PROJECT_URL=	http://www.iagora.com/~espel/rpm2cpio/
COMPONENT_SRC=		src

include ../../make-rules/prep.mk

# Do not clean the sources (set in prep.mk)
#
CLEAN_PATHS=

include ../../make-rules/ips.mk

CLEAN_PATHS+= $(BUILD_DIR)

# Common targets
#
build:
	# Just create the build directory, which is needed for publishing.
	# There is nothing to actually build.
	#
	$(RM) -r $(BUILD_DIR) ; $(MKDIR) $(BUILD_DIR)

install:
	@echo "Nothing to install."

test: $(NO_TESTS)

BUILD_PKG_DEPENDENCIES =	$(BUILD_TOOLS)

include ../../make-rules/depend.mk
