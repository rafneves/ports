# $OpenBSD: Makefile,v 1.13 2019/04/25 19:33:06 rsadowski Exp $

COMMENT=		Python IDE based on IntelliJ IDEA

V=			2019.1.1
DISTNAME=		pycharm-community-${V}
PKGNAME=		pycharm-${V}
CATEGORIES=		devel

HOMEPAGE=		https://www.jetbrains.com/pycharm/

MAINTAINER =		Rafael Sadowski <rsadowski@openbsd.org>

# Apache v2.0
PERMIT_PACKAGE_CDROM=	Yes

MASTER_SITES=		https://download.jetbrains.com/python/

MODULES=		java
MODJAVA_VER=		1.8+

BUILD_DEPENDS=		${MODJAVA_RUN_DEPENDS}

RUN_DEPENDS=		devel/desktop-file-utils \
			java/javaPathHelper

NO_TEST=		Yes

PC=			${PREFIX}/pycharm

# If NO_BUILD is set, JAVA_HOME doesn't get defined. So do
# a no-op for do-build.
do-build:
	@true

do-install:
	${INSTALL_DATA_DIR} ${PC}
	@tar -czf - -C ${WRKDIST} . | tar xzf - -C ${PC}
	@rm -rf ${PC}/jre
	@rm -rf ${PC}/jre64
	@rm -rf ${PC}/plugins/android
	@rm -rf ${PC}/lib/pty4j-native
	@rm -rf ${PC}/plugins/gradle/lib/native-platform-{freebsd,linux,osx,windows}*.jar
	@${SUBST_PROGRAM} ${FILESDIR}/pycharm ${PREFIX}/bin/pycharm
	@chmod ${BINMODE} ${PREFIX}/bin/pycharm
	${INSTALL_DATA_DIR} ${PREFIX}/share/applications
	cd ${WRKDIST}/lib && ${JAVA_HOME}/bin/jar xf icons.jar
	${INSTALL_DATA} ${WRKDIST}/lib/icon.png ${PC}/pycharm.png
	@${SUBST_DATA} ${FILESDIR}/pycharm.desktop \
		${PREFIX}/share/applications/pycharm.desktop
	${INSTALL_MAN} ${FILESDIR}/pycharm.1 ${PREFIX}/man/man1

.include <bsd.port.mk>
