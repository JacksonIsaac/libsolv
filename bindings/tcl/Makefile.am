noinst_LTLIBRARIES = libsolver.la
solvdir = $(prefix)/lib/tcl8/8.5
noinstdir = /opt/libsolv

noinst_DATA = $(solvdir)/solv-@VERSION@.dylib
CLEANFILES = $(solvdir)/solv-@VERSION@.dylib

$(solvdir)/solv-@VERSION@-1.dylib: $(noinstdir)/libsolver.dylib
	cp $< $@

AUTOMAKE_OPTIONS = subdir-objects

libsolver_la_SOURCES = solv_tcl.c
libsolver_la_CPPFLAGS = -I$(srcdir)/../../src -I../../src -I$(srcdir)/../../ext -I../../ext $(TCL_INCLUDE_SPEC)
libsolver_la_LDFLAGS = -avoid-version -shared $(TCL_LIB_SPEC)
libsolver_la_LIBADD = ../../src/libsolv.la ../../ext/libsolvext.la

# Create Tcl module to load libsolv.
solv.tm: solv.tm.in
	sed -e "s/__VERSION__/@VERSION@" solv.tm.in >$(noinstdir)/solv-@VERSION@.tm

#solv_tcl_SWIGFLAGS = -DHAVE_FUNOPEN -namespace -pkgversion $(VERSION)
solv_tcl_SWIGFLAGS = -namespace -pkgversion @VERSION@
solv_tcl.c: ../solv.i
	$(SWIG) $(solv_tcl_SWIGFLAGS) -tcl -I$(srcdir)/../../src -o $@ $<
