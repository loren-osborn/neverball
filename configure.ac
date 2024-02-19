AC_INIT([Neverball], [1.6.0], [support@neverball.org])
AC_CONFIG_SRCDIR([src/neverball.c])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
AC_PROG_CC
AC_PROG_CXX
AC_PROG_RANLIB

# Checks for libraries.
PKG_CHECK_MODULES([SDL2], [sdl2 >= 2.0.0])
PKG_CHECK_MODULES([SDL2_TTF], [SDL2_ttf >= 2.0.0])
PKG_CHECK_MODULES([VORBIS], [vorbis >= 1.3.0])
PKG_CHECK_MODULES([JPEG], [libjpeg >= 9.0])
PKG_CHECK_MODULES([CURL], [libcurl >= 7.0.0])

# Checks for header files.
AC_CHECK_HEADERS([stdlib.h stdio.h])

# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.
AC_CHECK_FUNCS([memset])

AC_ARG_ENABLE([gui-builds],
              [AS_HELP_STRING([--disable-gui-builds],[Disable building project files for GUI IDEs])],
              [enable_gui_builds=no],[enable_gui_builds=yes])

AS_CASE([$host], [*-mingw*|*-cygwin*], [os_windows=yes], [os_windows=no])

if test "x$enable_gui_builds" = "xno" -o "x$os_windows" = "xyes"; then
  AC_CHECK_PROG([CMAKE_FOUND], [cmake], [yes], [no])
  AS_IF([test "x$CMAKE_FOUND" = "xno"], [AC_MSG_ERROR([CMake is required but it's not installed.])])
fi

if test "x$os_windows" != "xyes"; then
    AC_CHECK_PROG([MAKE], [make], [yes])
    AS_IF([test "x$MAKE" = "xyes"], [
        AC_MSG_CHECKING([for GNU Make])
        AS_IF([make --version | grep GNU > /dev/null 2>&1], [
            AC_MSG_RESULT([yes])
        ], [
            AC_MSG_ERROR([GNU Make is required.])
        ])
    ])
fi

dnl Check for GNU m4
AC_CHECK_PROG(M4_FOUND, m4, yes, no)
AS_IF([test "$M4_FOUND" = "yes"], [
  AS_IF([m4 --version | grep '1.4.19' > /dev/null], [], [AC_MSG_ERROR([GNU m4 version 1.4.19 is required.])])
])

dnl Check for GNU Autoconf
AC_CHECK_PROG(AUTOCONF_FOUND, autoconf, yes, no)
AS_IF([test "$AUTOCONF_FOUND" = "yes"], [
  AS_IF([autoconf --version | grep '2.72' > /dev/null], [], [AC_MSG_ERROR([GNU Autoconf version 2.72 is required.])])
])

dnl Check for GNU Automake
AC_CHECK_PROG(AUTOMAKE_FOUND, automake, yes, no)
AS_IF([test "$AUTOMAKE_FOUND" = "yes"], [
  AS_IF([automake --version | grep '1.16.5' > /dev/null], [], [AC_MSG_ERROR([GNU Automake version 1.16.5 is required.])])
])

dnl Check for GNU Libtool
AC_CHECK_PROG(LIBTOOL_FOUND, libtool, yes, no)
AS_IF([test "$LIBTOOL_FOUND" = "yes"], [
  AS_IF([libtool --version | grep '2.4.7' > /dev/null], [], [AC_MSG_ERROR([GNU Libtool version 2.4.7 is required.])])
])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT


