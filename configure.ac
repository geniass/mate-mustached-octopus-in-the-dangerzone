# ================= initialization =================== #

AC_INIT([MATE System Resource Monitor Applet], [1.0.0], [http://www.mate-desktop.org],
[mate-resource-monitor])

AC_CONFIG_SRCDIR([src/resource-monitor-applet.c])
AM_CONFIG_HEADER([src/config.h])
AM_INIT_AUTOMAKE
AM_MAINTAINER_MODE

# ============== basic compiler settings ============= #
AC_PROG_CC
AC_HEADER_STDC

# =================== for plugins ==================== #
AC_PROG_LIBTOOL

# =========== take care of some localization ========= #
#AH_TEMPLATE([GETTEXT_PACKAGE], [Package name for gettext])
#GETTEXT_PACKAGE=mate-sensors-applet
#AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE")
#AC_SUBST(GETTEXT_PACKAGE)
#ALL_LINGUAS="cs de es fi fr hu it pl pt_BR ro ru sv zh_CN"
#AM_GLIB_GNU_GETTEXT
#AC_PROG_INTLTOOL

# ========== export compiler / linker options ======== #
AC_SUBST(CFLAGS)
AC_SUBST(CPPFLAGS)
AC_SUBST(LDFLAGS)
AC_SUBST(LIBS)

# ============== look for dependencies =============== #
# check for headers needed for standard interfaces
AC_CHECK_HEADERS(
	stdlib.h \
	string.h \ 
	stdio.h \
	sys/types.h \ 
	sys/socket.h \
	netinet/in.h \
	arpa/inet.h \
	fcntl.h \
	sys/ioctl.h \
	unistd.h \
	dlfcn.h
)   

GLIB_REQUIRED=2.26.0
GTK_REQUIRED=2.14.0
LIBPANEL_REQUIRED=1.1.0
#LIBMATENOTIFY_REQUIRED=1.1.0
LIBCAIRO_REQUIRED=1.0.4
LIBDBUSGLIB_REQUIRED=0.80
#LIBATASMART_REQUIRED=0.16

PKG_CHECK_MODULES(GLIB, glib-2.0 >= $GLIB_REQUIRED gio-2.0)
AC_SUBST(GLIB_CFLAGS)
AC_SUBST(GLIB_LIBS)

PKG_CHECK_MODULES(GTK, gtk+-2.0 >= $GTK_REQUIRED)
AC_SUBST(GTK_CFLAGS)
AC_SUBST(GTK_LIBS)

PKG_CHECK_MODULES(MATE, libmatepanelapplet-4.0 >= $LIBPANEL_REQUIRED)
AC_SUBST(MATE_CFLAGS)
AC_SUBST(MATE_LIBS)

PKG_CHECK_MODULES(CAIRO, cairo >= $LIBCAIRO_REQUIRED)
AC_SUBST(CAIRO_CFLAGS)
AC_SUBST(CAIRO_LIBS)
AC_SUBST(CFLAGS)
# for help docs stuff
AC_PATH_PROG(XSLTPROC, xsltproc, no)
if test x"$XSLTPROC" = xno; then
  AC_MSG_ERROR([xsltproc executable not found in your path - should be installed with libxslt])
fi

MATE_COMPILE_WARNINGS(maximum)

# ================ mate-doc-utils stuff ============= #
MATE_DOC_INIT

# ================ GSettings stuff ============= #
GLIB_GSETTINGS

# ==================== plugin stuff ================== #
PLUGIN_LIBTOOL_FLAGS="-module -avoid-version"
AC_SUBST(PLUGIN_LIBTOOL_FLAGS)

# ================= generate files =================== #
AC_CONFIG_FILES([
	Makefile
	src/Makefile
])
	#lib/Makefile
	#plugins/Makefile
	#plugins/acpi/Makefile
	#plugins/udisks/Makefile
	#plugins/eee/Makefile
	#plugins/hddtemp/Makefile
	#plugins/i2c-proc/Makefile
	#plugins/i2c-sys/Makefile
	#plugins/i8k/Makefile
	#plugins/ibm-acpi/Makefile
	#plugins/libsensors/Makefile
	#plugins/nvidia/Makefile
	#plugins/aticonfig/Makefile
	#plugins/omnibook/Makefile
	#plugins/pmu-sys/Makefile
	#plugins/smu-sys/Makefile
	#plugins/sonypi/Makefile
	#pixmaps/Makefile
	#po/Makefile.in
	#help/Makefile
#])
AC_OUTPUT
