# $OpenBSD: Makefile,v 1.5 2019/01/17 10:13:40 bentley Exp $

COMMENT =	efficient hex editor

DISTNAME =	tweak-3.02
REVISION =	1

CATEGORIES =	editors

HOMEPAGE =	https://www.chiark.greenend.org.uk/~sgtatham/tweak/

MAINTAINER =	Frederic Cambus <fcambus@openbsd.org>

# BSD
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB += c ncurses

MASTER_SITES =	https://www.chiark.greenend.org.uk/~sgtatham/tweak/

MAKE_FLAGS =	CC="${CC}" LINK="${CC}" CFLAGS="${CFLAGS} -c -Dunix"

FAKE_FLAGS =	PREFIX=${WRKINST}/${TRUEPREFIX}

USE_GMAKE =	Yes

NO_TEST =	Yes

.include <bsd.port.mk>
