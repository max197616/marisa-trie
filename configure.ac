#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.67])
AC_INIT([marisa], [0.2.5], [susumu.yata@gmail.com])
AC_CONFIG_SRCDIR([include/marisa.h])
AC_CONFIG_AUX_DIR([.])
AM_INIT_AUTOMAKE([foreign])

# Checks for programs.
LT_INIT
AC_PROG_CXX
AC_PROG_INSTALL

AC_CONFIG_MACRO_DIR([m4])

# Macros for SSE availability check.
AC_DEFUN([MARISA_ENABLE_SSE2],
          [AC_EGREP_CPP([yes], [
#ifdef __SSE2__
yes
#endif
          ], [enable_sse2="yes"], [enable_sse2="no"])])
AC_DEFUN([MARISA_ENABLE_SSE3],
          [AC_EGREP_CPP([yes], [
#ifdef __SSE3__
yes
#endif
          ], [enable_sse3="yes"], [enable_sse3="no"])])
AC_DEFUN([MARISA_ENABLE_SSSE3],
         [AC_EGREP_CPP([yes], [
#ifdef __SSSE3__
yes
#endif
         ], [enable_ssse3="yes"], [enable_ssse3="no"])])
AC_DEFUN([MARISA_ENABLE_SSE4_1],
         [AC_EGREP_CPP([yes], [
#ifdef __SSE4_1__
yes
#endif
         ], [enable_sse4_1="yes"], [enable_sse4_1="no"])])
AC_DEFUN([MARISA_ENABLE_SSE4_2],
         [AC_EGREP_CPP([yes], [
#ifdef __SSE4_2__
yes
#endif
         ], [enable_sse4_2="yes"], [enable_sse4_2="no"])])
AC_DEFUN([MARISA_ENABLE_SSE4],
         [AC_EGREP_CPP([yes], [
#if defined(__POPCNT__) && defined(__SSE4_2__)
yes
#endif
         ], [enable_sse4="yes"], [enable_sse4="no"])])
AC_DEFUN([MARISA_ENABLE_SSE4A],
         [AC_EGREP_CPP([yes], [
#ifdef __SSE4A__
yes
#endif
         ], [enable_sse4a="yes"], [enable_sse4a="no"])])
AC_DEFUN([MARISA_ENABLE_AVX],
         [AC_EGREP_CPP([yes], [
#ifdef __AVX__
yes
#endif
         ], [enable_avx="yes"], [enable_avx="no"])])
AC_DEFUN([MARISA_ENABLE_AVX2],
         [AC_EGREP_CPP([yes], [
#ifdef __AVX2__
yes
#endif
         ], [enable_avx2="yes"], [enable_avx2="no"])])
AC_DEFUN([MARISA_ENABLE_POPCNT],
         [AC_EGREP_CPP([yes], [
#ifdef __POPCNT__
yes
#endif
         ], [enable_popcnt="yes"], [enable_popcnt="no"])])

# Enable native cpu instructions.
AC_MSG_CHECKING([whether to enable optimization for native cpu])
AC_ARG_ENABLE([native-code],
              [AS_HELP_STRING([--enable-native-code],
                              [generate instructions for native cpu [default=no]])],
              [],
              [enable_native_code="no"])
AS_IF([test "x${enable_native_code}" != "xno"], [
  CFLAGS="$CPPFLAGS -march=native"
  CPPFLAGS="$CPPFLAGS -march=native"
  CXXFLAGS="$CXXFLAGS -march=native"
  MARISA_ENABLE_SSE2
  MARISA_ENABLE_SSE3
  MARISA_ENABLE_SSE4_1
  MARISA_ENABLE_SSE4_2
  MARISA_ENABLE_SSE4
  MARISA_ENABLE_SSE4A
  MARISA_ENABLE_AVX
  MARISA_ENABLE_AVX2
  MARISA_ENABLE_POPCNT
])
AC_MSG_RESULT([${enable_native_code}])

# Checks for SSE availability.
AC_MSG_CHECKING([whether to use SSE2])
AC_ARG_ENABLE([sse2],
              [AS_HELP_STRING([--enable-sse2],
                              [use SSE2 [default=no]])],
              [],
              [enable_sse2="no"])
AS_IF([test "x${enable_sse2}" != "xno"], [MARISA_ENABLE_SSE2])
AC_MSG_RESULT([${enable_sse2}])

AC_MSG_CHECKING([whether to use SSE3])
AC_ARG_ENABLE([sse3],
              [AS_HELP_STRING([--enable-sse3],
                              [use SSE3 [default=no]])],
              [],
              [enable_sse3="no"])
AS_IF([test "x${enable_sse3}" != "xno"], [MARISA_ENABLE_SSE3])
AC_MSG_RESULT([${enable_sse3}])

AC_MSG_CHECKING([whether to use SSSE3])
AC_ARG_ENABLE([ssse3],
              [AS_HELP_STRING([--enable-ssse3],
                              [use SSSE3 [default=no]])],
              [],
              [enable_ssse3="no"])
AS_IF([test "x${enable_ssse3}" != "xno"], [MARISA_ENABLE_SSSE3])
AC_MSG_RESULT([${enable_ssse3}])

AC_MSG_CHECKING([whether to use SSE4.1])
AC_ARG_ENABLE([sse4.1],
              [AS_HELP_STRING([--enable-sse4.1],
                              [use SSE4.1 [default=no]])],
              [],
              [enable_sse4_1="no"])
AS_IF([test "x${enable_sse4_1}" != "xno"], [MARISA_ENABLE_SSE4_1])
AC_MSG_RESULT([${enable_sse4_1}])

AC_MSG_CHECKING([whether to use SSE4.2])
AC_ARG_ENABLE([sse4.2],
              [AS_HELP_STRING([--enable-sse4.2],
                              [use SSE4.2 [default=no]])],
              [],
              [enable_sse4_2="no"])
AS_IF([test "x${enable_sse4_2}" != "xno"], [MARISA_ENABLE_SSE4_2])
AC_MSG_RESULT([${enable_sse4_2}])

AC_MSG_CHECKING([whether to use SSE4])
AC_ARG_ENABLE([sse4],
              [AS_HELP_STRING([--enable-sse4],
                              [use SSE4 [default=no]])],
              [],
              [enable_sse4="no"])
AS_IF([test "x${enable_sse4}" != "xno"], [MARISA_ENABLE_SSE4])
AC_MSG_RESULT([${enable_sse4}])

AC_MSG_CHECKING([whether to use SSE4a])
AC_ARG_ENABLE([sse4a],
              [AS_HELP_STRING([--enable-sse4a],
                              [use SSE4a [default=no]])],
              [],
              [enable_sse4a="no"])
AS_IF([test "x${enable_sse4a}" != "xno"], [MARISA_ENABLE_SSE4A])
AC_MSG_RESULT([${enable_sse4a}])
AC_ARG_ENABLE([avx],
              [AS_HELP_STRING([--enable-avx],
                              [use AVX [default=no]])],
              [],
              [enable_avx="no"])
AS_IF([test "x${enable_avx}" != "xno"], [MARISA_ENABLE_AVX])
AC_MSG_RESULT([${enable_avx}])
AC_ARG_ENABLE([avx2],
              [AS_HELP_STRING([--enable-avx2],
                              [use AVX2 [default=no]])],
              [],
              [enable_avx2="no"])
AS_IF([test "x${enable_avx2}" != "xno"], [MARISA_ENABLE_AVX2])
AC_MSG_RESULT([${enable_avx2}])

AC_MSG_CHECKING([whether to use popcnt])
AC_ARG_ENABLE([popcnt],
              [AS_HELP_STRING([--enable-popcnt],
                              [use POPCNT [default=no]])],
              [],
              [enable_popcnt="no"])
AS_IF([test "x${enable_popcnt}" != "xno"], [MARISA_ENABLE_POPCNT])
AC_MSG_RESULT([${enable_popcnt}])

AS_IF([test "x${enable_popcnt}" != "xno"], [
  enable_sse3="yes"
])
AS_IF([test "x${enable_avx}" != "xno"], [
  enable_popcnt="yes"
])
AS_IF([test "x${enable_avx2}" != "xno"], [
  enable_popcnt="yes"
  enable_avx="yes"
])
AS_IF([test "x${enable_sse4a}" != "xno"], [
  enable_popcnt="yes"
  enable_sse3="yes"
])
AS_IF([test "x${enable_sse4}" != "xno"], [
  enable_popcnt="yes"
  enable_sse4_2="yes"
])
AS_IF([test "x${enable_sse4_2}" != "xno"], [
  enable_popcnt="yes"
  enable_sse4_1="yes"
])
AS_IF([test "x${enable_sse4_1}" != "xno"], [
  enable_ssse3="yes"
])
AS_IF([test "x${enable_ssse3}" != "xno"], [
  enable_sse3="yes"
])
AS_IF([test "x${enable_sse3}" != "xno"], [
  enable_sse2="yes"
])

AS_IF([test "x${enable_popcnt}" != "xno"], [
  CXXFLAGS="$CXXFLAGS -DMARISA_USE_POPCNT -mpopcnt"
])
if test "x${enable_avx2}" != "xno"; then
  CXXFLAGS="$CXXFLAGS -DMARISA_USE_AVX2 -mavx2"
elif test "x${enable_avx}" != "xno"; then
  CXXFLAGS="$CXXFLAGS -DMARISA_USE_AVX -mavx"
elif test "x${enable_sse4a}" != "xno"; then
  CXXFLAGS="$CXXFLAGS -DMARISA_USE_SSE4A -msse4a"
elif test "x${enable_sse4}" != "xno"; then
  CXXFLAGS="$CXXFLAGS -DMARISA_USE_SSE4 -msse4"
elif test "x${enable_sse4_2}" != "xno"; then
  CXXFLAGS="$CXXFLAGS -DMARISA_USE_SSE4_2 -msse4.2"
elif test "x${enable_sse4_1}" != "xno"; then
  CXXFLAGS="$CXXFLAGS -DMARISA_USE_SSE4_1 -msse4.1"
elif test "x${enable_ssse3}" != "xno"; then
  CXXFLAGS="$CXXFLAGS -DMARISA_USE_SSSE3 -mssse3"
elif test "x${enable_sse3}" != "xno"; then
  CXXFLAGS="$CXXFLAGS -DMARISA_USE_SSE3 -msse3"
elif test "x${enable_sse2}" != "xno"; then
  CXXFLAGS="$CXXFLAGS -DMARISA_USE_SSE2 -msse2"
fi

AC_CONFIG_FILES([Makefile
                 marisa.pc
                 include/Makefile
                 include/marisa/Makefile
                 lib/Makefile
                 lib/marisa/Makefile
                 lib/marisa/grimoire/Makefile
                 lib/marisa/grimoire/algorithm/Makefile
                 lib/marisa/grimoire/io/Makefile
                 lib/marisa/grimoire/trie/Makefile
                 lib/marisa/grimoire/vector/Makefile
                 tests/Makefile
                 tools/Makefile])
AC_OUTPUT

AS_ECHO([])
AS_ECHO(["${PACKAGE_NAME} ${PACKAGE_VERSION} configuration:"])
AS_ECHO(["-------------------------------"])
AS_ECHO(["  HOST:      ${host}"])
AS_ECHO(["  CXX:       ${CXX}"])
AS_ECHO(["  CXXFLAGS:  ${CXXFLAGS}"])
AS_ECHO(["  LDFLAGS:   ${LDFLAGS}"])
AS_ECHO(["  PREFIX:    ${prefix}"])
AS_ECHO([])
AS_ECHO(["  NATIVE:    ${enable_native_code}"])
AS_ECHO(["  SSE2:      ${enable_sse2}"])
AS_ECHO(["  SSE3:      ${enable_sse3}"])
AS_ECHO(["  SSSE3:     ${enable_ssse3}"])
AS_ECHO(["  SSE4.1:    ${enable_sse4_1}"])
AS_ECHO(["  SSE4.2:    ${enable_sse4_2}"])
AS_ECHO(["  SSE4a:     ${enable_sse4a}"])
AS_ECHO(["  AVX:       ${enable_avx}"])
AS_ECHO(["  AVX2:      ${enable_avx2}"])
AS_ECHO(["  POPCNT:    ${enable_popcnt}"])
AS_ECHO([])
