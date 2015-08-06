noinst_LTLIBRARIES = libsolver.la
noinstdir = /opt/libsolv

noinst_DATA = $(noinstdir)/solv-@VERSION@.dylib
CLEANFILES = $(noinstdir)/solv-@VERSION@.dylib

$(noinstdir)/solv-@VERSION@.dylib: $(noinstdir)/libsolver.dylib
	cp $< $@

AUTOMAKE_OPTIONS = subdir-objects
#lib_LTLIBRARIES = libsolver.la

libsolver_la_SOURCES = solv_tcl.c
libsolver_la_CPPFLAGS = -I$(srcdir)/../../src -I../../src -I$(srcdir)/../../ext -I../../ext $(TCL_INCLUDE_SPEC)
libsolver_la_LDFLAGS = -avoid-version -shared $(TCL_LIB_SPEC)
libsolver_la_LIBADD = ../../src/libsolv.la ../../ext/libsolvext.la

#solv_tcl_SWIGFLAGS = -DHAVE_FUNOPEN -namespace -pkgversion $(VERSION)
solv_tcl_SWIGFLAGS = -namespace -pkgversion @VERSION@
solv_tcl.c: ../solv.i
	$(SWIG) $(solv_tcl_SWIGFLAGS) -tcl -I$(srcdir)/../../src -o $@ $<
