AC_INIT([libsolv],[0.6.11],[macports-dev@lists.macosforge.org])
AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE([foreign -Wall -Werror subdir-objects])
AM_PROG_AR
LT_INIT
AC_PROG_CC

# Set swig Macros
AX_PKG_SWIG

# Set Tcl Macros
SC_PATH_TCLCONFIG
SC_LOAD_TCLCONFIG

# Check function exists or not
AC_CHECK_FUNCS([qsort_r __qsort_r strchrnul fopencookie funopen])


# Configure Libsolv version.
LIBSOLV_MAJOR=$(echo "${PACKAGE_VERSION}" | cut -d . -f 1)
LIBSOLV_MINOR=$(echo "${PACKAGE_VERSION}" | cut -d . -f 2)
LIBSOLV_PATCH=$(echo "${PACKAGE_VERSION}" | cut -d . -f 3)

VERSION=$PACKAGE_VERSION

AC_SUBST([VERSION])
AC_SUBST([LIBSOLV_MAJOR])
AC_SUBST([LIBSOLV_MINOR])
AC_SUBST([LIBSOLV_PATCH])

AC_CONFIG_FILES(Makefile src/Makefile ext/Makefile bindings/Makefile bindings/tcl/Makefile src/solvversion.h)
AC_OUTPUT
