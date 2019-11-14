# Copyright (C) 2009 International Business Machines.
# All Rights Reserved.
# This file is distributed under the Eclipse Public License.

# Author:  Andreas Waechter            IBM    2009-04-20

#############################################################################
#                       Names and other basic things                        #
#############################################################################

AC_PREREQ(2.59)

AC_INIT([ThirdPartyMetis],[2.0.1],[https://github.com/coin-or-tools/ThirdParty-Metis/issues/new],,[https://github.com/coin-or-tools/ThirdParty-Metis])

AC_COPYRIGHT([
Copyright 2009 International Business Machines and others.
All Rights Reserved.
This file is part of the open source package ThirdParty-Metis which is distributed
under the Eclipse Public License.])

# List one file in the package so that the configure script can test
# whether the package is actually there
AC_CONFIG_SRCDIR(metis-4.0/Lib/balance.c)

AC_COIN_INITIALIZE(Metis)

#############################################################################
#                         Standard build tool stuff                         #
#############################################################################

AC_COIN_PROG_CC

# Initialize libtool
# Disable win32-dll, so we get all Metis symbols exported with a DLL.
AC_COIN_PROG_LIBTOOL(no-win32-dll)

# Metis depends on libm
AC_COIN_CHK_LIBM(Metis)

# We may need to create a dummy header file for Windows
AC_CHECK_HEADER([strings.h], [], [touch strings.h])
AM_CONDITIONAL(INSTALL_STRINGS_H, test -f strings.h)

# On some systems, there are no drand48 and srand48.
# By defining __VC__, we can make Metis use an alternative function
AC_CHECK_FUNC(drand48,,[CFLAGS="$CFLAGS -D__VC__"])

METISDIR=metis-4.0
AC_SUBST(METISDIR)

AC_CONFIG_FILES([Makefile coinmetis.pc])

AC_COIN_FINALIZE_FLAGS([Metis])

AC_COIN_FINALIZE
