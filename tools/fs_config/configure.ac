AC_INIT([fsconfig-native], 1.0.0)
AM_INIT_AUTOMAKE([foreign])

AC_PROG_CC
AM_PROG_CC_C_O
AC_PROG_CPP
PKG_PROG_PKG_CONFIG

AC_SUBST([CUTILS_CFLAGS])
AC_SUBST([CUTILS_LIBS])

AC_ARG_ENABLE([selinux],
  [AS_HELP_STRING([--enable-selinux], [Enable SELinux support])],
  [], [enable_selinux=no])

AS_IF([test "x$enable_selinux" = "xyes"], [
  PKG_CHECK_MODULES([LIBSELINUX], [libselinux])
  AC_SUBST([LIBSELINUX_CFLAGS])
  AC_SUBST([LIBSELINUX_LIBS])
  AC_DEFINE([HAVE_SELINUX], [1], [Define if SELinux support is enabled])
])

AM_CONDITIONAL(USE_GLIB, test "x${with_glib}" = "xyes")


AC_ARG_WITH([core-headers],
      AC_HELP_STRING([--with-core-headers=@<:@dir@:>@],
         [Specify the location of the system core headers]),
      [CPPFLAGS="$CPPFLAGS -I$withval"],
      with_core-headers=no)

AC_ARG_WITH([sanitized-headers],
      AC_HELP_STRING([--with-sanitized-headers=@<:@dir@:>@],
         [Specify the location of the sanitized Linux kernel headers]),
      [CPPFLAGS="$CPPFLAGS -idirafter $withval"],
      with_sanitized-headers=no)

AC_CONFIG_FILES([     \
        Makefile    \
        ])

AC_OUTPUT
