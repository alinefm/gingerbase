#
# Ginger Base
#
# Copyright IBM Corp, 2015
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA

AC_INIT([gingerbase], [m4_esyscmd([./build-aux/pkg-version --version])])

AC_SUBST([PACKAGE_VERSION],
         [m4_esyscmd([./build-aux/pkg-version --version])])

AC_SUBST([PACKAGE_RELEASE],
         [m4_esyscmd([./build-aux/pkg-version --release])])

# Testing for version and release
AS_IF([test "x$PACKAGE_VERSION" = x],
      AC_MSG_ERROR([package version not defined]))
AS_IF([test "x$PACKAGE_RELEASE" = x],
      AC_MSG_ERROR([package release not defined]))

AC_CONFIG_AUX_DIR([build-aux])
AM_INIT_AUTOMAKE([-Wno-portability])
AM_PATH_PYTHON([2.6])
AC_PATH_PROG([PEP8], [pep8], [/usr/bin/pep8])
AC_PYTHON_MODULE([unittest])
AC_SUBST([HAVE_PYMOD_UNITTEST])
AC_SUBST([PYTHON_VERSION])
AM_GNU_GETTEXT([external])
AM_GNU_GETTEXT_VERSION([0.10])
AC_PATH_PROG([CHEETAH], [cheetah], [/usr/bin/cheetah])

# Checking for pyflakes
AC_PATH_PROG([PYFLAKES], [pyflakes])
if test "x$PYFLAKES" = "x"; then
  AC_MSG_WARN([pyflakes not found])
fi

AC_ARG_ENABLE(
    [sample],
    [AS_HELP_STRING(
        [--enable-sample],
        [enable sample plugin @<:@default=no@:>@]
    )],
    ,
    [enable_sample="no"]
)

if test "${enable_sample}" = "yes"; then
AC_SUBST([ENABLE_SAMPLE], [True])
else
AC_SUBST([ENABLE_SAMPLE], [False])
fi

AC_CONFIG_FILES([
    po/Makefile.in
    po/gen-pot
    Makefile
    docs/Makefile
    control/Makefile
    model/Makefile
    ui/Makefile
    ui/config/Makefile
    ui/css/Makefile
    ui/images/Makefile
    ui/js/Makefile
    ui/pages/Makefile
    ui/pages/help/Makefile
    ui/pages/help/en_US/Makefile
    ui/pages/help/de_DE/Makefile
    ui/pages/help/es_ES/Makefile
    ui/pages/help/fr_FR/Makefile
    ui/pages/help/it_IT/Makefile
    ui/pages/help/ja_JP/Makefile
    ui/pages/help/ko_KR/Makefile
    ui/pages/help/pt_BR/Makefile
    ui/pages/help/ru_RU/Makefile
    ui/pages/help/zh_CN/Makefile
    ui/pages/help/zh_TW/Makefile
    contrib/Makefile
    contrib/DEBIAN/Makefile
    contrib/DEBIAN/control
    contrib/gingerbase.spec.fedora
    contrib/gingerbase.spec.suse
    tests/Makefile
],[
    chmod +x po/gen-pot
])

AC_OUTPUT
