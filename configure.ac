dnl Process this file with `autoconf' to produce a configure script.
#AC_INIT(lib/tv.h)
#AM_INIT_AUTOMAKE(tvision, 0.8)
AC_INIT([tvision], [0.8])
AC_CONFIG_SRCDIR([lib/tv.h])
AM_INIT_AUTOMAKE

AM_CONFIG_HEADER(config.h)
AC_CONFIG_MACRO_DIR([m4])

dnl Check for system.
AC_CANONICAL_HOST

dnl Checks for programs.
AC_PROG_CC
AC_PROG_CXX
AC_PROG_CPP

dnl Checks for header files.
AC_STDC_HEADERS
AC_CHECK_HEADERS(ncurses.h curses.h gpm.h)

dnl Checks for libraries.
AC_CHECK_LIB(ncurses, initscr, ,
	[AC_CHECK_LIB(curses, initscr)])

dnl Checks for library functions.
AC_CHECK_LIB(gpm, Gpm_Close)
dnl AC_CHECK_LIB(mytinfo, ???)

dnl Checks for dynamic libraries.
dnl AM_PROG_RANLIB
AM_PROG_LIBTOOL
AC_PROG_RANLIB

dnl Various enable/disable checks.

AC_MSG_CHECKING(if the Russian character set should be enabled (now obsolete))
AC_ARG_ENABLE(russian,
[  --enable-russian        enable Russian character set (now obsolete)],
[
AC_MSG_RESULT(yes)
AC_DEFINE(ENABLE_RUSSIAN_CHARSET)
], [
AC_MSG_RESULT(no)
])

AC_MSG_CHECKING(if the alternate character set should be disabled)
AC_ARG_ENABLE(acs,
[  --disable-acs           disable alternate character set],
[
AC_MSG_RESULT(yes)
AC_DEFINE(DISABLE_ACS)
], [
AC_MSG_RESULT(no)
])

AC_MSG_CHECKING(if the 8 bit output should be disabled)
AC_ARG_ENABLE(8bit,
[  --disable-8bit          disable 8 bit output],
[
AC_MSG_RESULT(yes)
AC_DEFINE(DISABLE_8BIT_CHARS)
], [
AC_MSG_RESULT(no)
])

case $host_os in
	linux*)
AC_MSG_CHECKING(if the Linux GPM mouse support should be disabled)
AC_ARG_ENABLE(linux-gpm,
[  --disable-linux-gpm     disable Linux GPM mouse support],
[
AC_MSG_RESULT(yes)
], [
AC_MSG_RESULT(no)
AC_DEFINE(ENABLE_GPM)
])

AC_MSG_CHECKING(if the Linux VCS support should be disabled)
AC_ARG_ENABLE(linux-vcs,
[  --disable-linux-vcs     disable Linux VCS support],
[
AC_MSG_RESULT(yes)
], [
AC_MSG_RESULT(no)
AC_DEFINE(ENABLE_VCS)
])
	;;
	freebsd*)
AC_MSG_CHECKING(if the FreeBSD mouse support should be disabled)
AC_ARG_ENABLE(freebsd-mouse,
[  --disable-freebsd-mouse disable FreeBSD mouse support],
[
AC_MSG_RESULT(yes)
], [
AC_MSG_RESULT(no)
AC_DEFINE(ENABLE_FBSDM)
])
	;;
esac

AC_OUTPUT(doc/Makefile lib/Makefile demo/Makefile tutorial/Makefile \
	tvhc/Makefile Makefile)
