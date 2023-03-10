dnl Process this file with autoconf to produce a configure script.
AC_INIT(src/atak.c)
AC_PREREQ(2.13)
AM_INIT_AUTOMAKE(gnuchess, 5.07)
AM_CONFIG_HEADER(src/config.h)

dnl Checks for programs.
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_AWK
AC_PROG_LN_S
AC_STRUCT_TM
AM_PROG_LEX

dnl --with and --enable things
AC_ARG_WITH(readline, 
	AC_HELP_STRING([--with-readline],
	[use readline library if available (default is YES)]),
	ac_cv_use_readline=$withval,
	ac_cv_use_readline=yes)

dnl Check for readline library _and_ headers
if test x"$ac_cv_use_readline" = "xyes"; then
	AC_CHECK_LIB(ncurses, tputs)
	AC_CHECK_LIB(readline, readline)
	AC_CHECK_HEADERS(readline/readline.h readline/history.h)
fi

dnl Checks for header files.
AC_HEADER_STDC

dnl Either we should make these checks fail with an
dnl AC_MSG_ERROR or we should treat missing headers
dnl with #ifdef somehow. (As it stands, it still gives
dnl valuable debugging info for bug reports, but not more.)
AC_CHECK_HEADERS(time.h sys/time.h unistd.h errno.h fcntl.h libintl.h)

dnl Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_C_VOLATILE
AC_FUNC_REALLOC
AC_HEADER_STDBOOL
AC_C_INLINE
AC_TYPE_SIZE_T
AC_HEADER_TIME
AX_CREATE_STDINT_H(src/GCint.h)

dnl Checks for library functions.
AC_TYPE_SIGNAL
AC_FUNC_MALLOC
AC_FUNC_MEMCMP

dnl See above, how do we treat failure here?
AC_CHECK_FUNCS(gettimeofday strchr strcspn strstr strerror memset strdup strtol)

dnl Don't Check for getopt_long 
dnl just use bundled version like hello does
dnl AC_SUBST(LIBOBJS)
dnl AC_CHECK_FUNCS(getopt_long , , [LIBOBJS="$LIBOBJS getopt.o getopt1.o"] )
ACX_PTHREAD()
AC_CONFIG_FILES(Makefile src/Makefile)
AC_OUTPUT
