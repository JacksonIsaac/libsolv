AUTOMAKE_OPTIONS = subdir-objects

noinst_LTLIBRARIES = libsolver.la
solvdir = $(prefix)/lib/tcl8/8.5

solv_DATA = $(solvdir)/solv-@VERSION@.dylib solv.tm
CLEANFILES = $(solvdir)/solv-@VERSION@.dylib

$(solvdir)/solv-@VERSION@-1.dylib: libsolver.dylib
	cp $< $@

libsolver_la_SOURCES = solv_tcl.c
libsolver_la_CPPFLAGS = -I$(srcdir)/../../src -I../../src -I$(srcdir)/../../ext -I../../ext $(TCL_INCLUDE_SPEC)
libsolver_la_LDFLAGS = -avoid-version -shared $(TCL_LIB_SPEC)
libsolver_la_LIBADD = ../../src/libsolv.la ../../ext/libsolvext.la

# Create Tcl module to load libsolv.
solv.tm: solv.tm.in
	sed -e "s/__VERSION__/@VERSION@/g" solv.tm.in >$(srcdir)/solv.tm

#solv_tcl_SWIGFLAGS = -DHAVE_FUNOPEN -namespace -pkgversion $(VERSION)
solv_tcl_SWIGFLAGS = -namespace -pkgversion @VERSION@
solv_tcl.c: ../solv.i
	$(SWIG) $(solv_tcl_SWIGFLAGS) -tcl -I$(srcdir)/../../src -o $@ $<
