# vim:set noet ts=4:
#
# ibus-hangul-jis - The Hangul engine for IBus
#
# Copyright (c) 2007-2008 Huang Peng <shawn.p.huang@gmail.com>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along
# with this program; if not, write to the Free Software Foundation, Inc.,
# 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

AM_CFLAGS = \
	@IBUS_CFLAGS@ \
	@HANGUL_CFLAGS@ \
	-DPKGDATADIR=\"$(pkgdatadir)\" \
	$(NULL)
AM_LDFLAGS = \
	@IBUS_LIBS@ \
	@HANGUL_LIBS@ \
	$(NULL)

noinst_LIBRARIES = \
	libinternal.a
	$(NULL)

libinternal_a_SOURCES = \
	engine.c \
	engine.h \
	ustring.c \
	ustring.h \
	i18n.h \
	$(NULL)

libinternal_a_CFLAGS = \
	@IBUS_CFLAGS@ \
	@HANGUL_CFLAGS@ \
	-DPKGDATADIR=\"$(pkgdatadir)\" \
	-DLOCALEDIR=\"$(localedir)\" \
	-DLIBEXECDIR=\"$(libexecdir)\" \
	-DIBUSHANGUL_DATADIR=\"$(datadir)/ibus-hangul-jis\" \
	$(NULL)

check_PROGRAMS = \
	test-ustring
	$(NULL)

TESTS = \
	$(check_PROGRAMS) \
	$(NULL)

libexec_PROGRAMS = ibus-engine-hangul-jis

ibus_engine_hangul_jis_SOURCES = \
	main.c \
	$(NULL)

ibus_engine_hangul_jis_CFLAGS = \
	@IBUS_CFLAGS@ \
	@HANGUL_CFLAGS@ \
	-DPKGDATADIR=\"$(pkgdatadir)\" \
	-DLOCALEDIR=\"$(localedir)\" \
	-DLIBEXECDIR=\"$(libexecdir)\" \
	-DIBUSHANGUL_DATADIR=\"$(datadir)/ibus-hangul-jis\" \
	$(NULL)

ibus_engine_hangul_jis_LDADD = \
	libinternal.a \
	@IBUS_LIBS@ \
	@HANGUL_LIBS@ \
	$(NULL)

component_DATA = \
	hanguljis.xml \
	$(NULL)
componentdir = $(datadir)/ibus/component

EXTRA_DIST = \
	$(NULL)

CLEANFILES = \
	hanguljis.xml \
	$(NULL)

hanguljis.xml: hanguljis.xml.in
	( \
		libexecdir=${libexecdir}; \
		pkgdatadir=${pkgdatadir}; \
		s=`cat $<`; \
		eval "echo \"$${s}\""; \
	) > $@

test: ibus-engine-hangul-jis
	$(builddir)/ibus-engine-hangul-jis

test_ustring_CFLAGS = $(IBUS_CFLAGS) $(HANGUL_CFLAGS)
test_ustring_LDADD = $(IBUS_LIBS)
test_ustring_SOURCES = test-ustring.c ustring.c ustring.h

check-local:
		$(builddir)/test-ustring
