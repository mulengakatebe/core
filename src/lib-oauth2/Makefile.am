AM_CPPFLAGS = \
	-I$(top_srcdir)/src/lib \
	-I$(top_srcdir)/src/lib-test \
	-I$(top_srcdir)/src/lib-http \
	-I$(top_srcdir)/src/lib-settings

noinst_LTLIBRARIES=liboauth2.la

pkginc_libdir=$(pkgincludedir)
pkginc_lib_HEADERS = \
	oauth2.h

noinst_HEADERS = \
	oauth2-private.h

liboauth2_la_SOURCES = \
	oauth2.c \
	oauth2-token-validate.c \
	oauth2-passwd-grant.c \
	oauth2-introspect.c \
	oauth2-refresh.c

test_programs = \
	test-oauth2-json

noinst_PROGRAMS = $(test_programs)

test_libs = \
	$(noinst_LTLIBRARIES) \
	../lib-http/libhttp.la \
	../lib-dns/libdns.la \
	../lib-ssl-iostream/libssl_iostream.la \
	../lib-master/libmaster.la \
	../lib-settings/libsettings.la \
	../lib-test/libtest.la \
	../lib/liblib.la \
	$(MODULE_LIBS)
test_deps = \
	$(noinst_LTLIBRARIES) \
	../lib-http/libhttp.la \
	../lib-dns/libdns.la \
	../lib-ssl-iostream/libssl_iostream.la \
	../lib-master/libmaster.la \
	../lib-settings/libsettings.la \
	../lib-test/libtest.la \
	../lib/liblib.la

test_oauth2_json_SOURCES = test-oauth2-json.c
test_oauth2_json_LDADD = $(test_libs)
test_oauth2_json_DEPENDENCIES = $(test_deps)

check-local:
	for bin in $(test_programs); do \
	  if ! $(RUN_TEST) ./$$bin; then exit 1; fi; \
	done

