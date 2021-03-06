#		
#  Makefile for the GNUstep LDAP Library
#
#  Copyright (C) 2002-2003 Free Software Foundation, Inc.
#
#  Written by:	Manuel Guesdon <mguesdon@orange-concept.com>
#
#  This file is part of the GNUstep LDAP Library.
#
#  This library is free software; you can redistribute it and/or
#  modify it under the terms of the GNU Library General Public
#  License as published by the Free Software Foundation; either
#  version 2 of the License, or (at your option) any later version.
#
#  This library is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.	 See the GNU
#  Library General Public License for more details.
#
#  You should have received a copy of the GNU Library General Public
#  License along with this library; if not, write to the Free
#  Software Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#

ifeq ($(GNUSTEP_MAKEFILES),)
 GNUSTEP_MAKEFILES := $(shell gnustep-config --variable=GNUSTEP_MAKEFILES 2>/dev/null)
  ifeq ($(GNUSTEP_MAKEFILES),)
    $(warning )
    $(warning Unable to obtain GNUSTEP_MAKEFILES setting from gnustep-config!)
    $(warning Perhaps gnustep-make is not properly installed,)
    $(warning so gnustep-config is not in your PATH.)
    $(warning )
    $(warning Your PATH is currently $(PATH))
    $(warning )
  endif
endif

ifeq ($(GNUSTEP_MAKEFILES),)
  $(error You need to set GNUSTEP_MAKEFILES before compiling!)
endif

include $(GNUSTEP_MAKEFILES)/common.make

PACKAGE_NAME = gsldap

# The Library to be compiled
LIBRARY_NAME = libgsldap

# The Objective-C source files to be compiled		
libgsldap_OBJC_FILES = \
GSLDAPUtils.m \
GSLDAPConnection.m \
GSLDAPEntry.m \
GSLDAPAttribute.m \
GSLDAPObjectClass.m \
GSLDAPSyntax.m \
GSLDAPMatchingRule.m \
GSLDAPSchema.m \


# The Library installed header files
libgsldap_HEADER_FILES = \
GSLDAPCom.h \
GSLDAPUtils.h \
GSLDAPConnection.h  \
GSLDAPEntry.h \
GSLDAPAttribute.h \
GSLDAPObjectClass.h \
GSLDAPSyntax.h \
GSLDAPMatchingRule.h \
GSLDAPSchema.h \

SRCS = $(TOOL_NAME:=.m) $(LIBRARY_NAME:=.m)	

HDRS = $(LIBRARY_NAME:=.h)

DIST_FILES = $(SRCS) $(HDRS) GNUmakefile Makefile.postamble Makefile.preamble
libgsldap_HEADER_FILES_DIR = $(HEADER_DIR)
libgsldap_HEADER_FILES_INSTALL_DIR = gsldap

gsldap_AUTOGSDOC_HEADERS = $(libgsldap_HEADER_FILES)
gsldap_AUTOGSDOC_SOURCE = $(libgsldap_OBJC_FILES)
DOCUMENT_NAME = gsldap
gsldap_AGSDOC_FILES = GSLDAP.gsdoc $(gsldap_AUTOGSDOC_HEADERS) 
#$(gsldap_AUTOGSDOC_SOURCE)
gsldap_AGSDOC_FLAGS = \
	-Declared Foundation \
	-Standards YES \
	-Project GSLDAP \
	-WordMap '{\
	FOUNDATION_EXPORT=extern;FOUNDATION_STATIC_INLINE="";\
	GS_GEOM_SCOPE=extern;GS_GEOM_ATTR="";\
	GS_EXPORT=extern;GS_DECLARE="";\
	GS_RANGE_SCOPE=extern;GS_RANGE_ATTR="";\
	GS_ZONE_SCOPE=extern;GS_ZONE_ATTR="";\
	}' -Up gsldap

#	-SystemProjects System \

-include Makefile.preamble
include $(GNUSTEP_MAKEFILES)/library.make
# Only build the doc if doc=yes was passed on the command line
ifeq ($(doc),yes)
include $(GNUSTEP_MAKEFILES)/documentation.make
endif

-include Makefile.postamble
