# $OpenBSD: Makefile,v 1.60 2019/04/26 12:38:02 rsadowski Exp $

COMMENT=		IntelliJ IDEA Java IDE

V=			2019.1.1
DISTNAME=		ideaIC-${V}
PKGNAME=		intellij-${V}
CATEGORIES=		devel

HOMEPAGE=		https://www.jetbrains.com/idea/
MAINTAINER=		Caspar Schutijser <caspar@schutijser.com>

# Apache v2.0
PERMIT_PACKAGE_CDROM=	Yes

MASTER_SITES=		https://download.jetbrains.com/idea/

MODULES=		java
MODJAVA_VER=		1.8+

BUILD_DEPENDS=		${MODJAVA_RUN_DEPENDS}

RUN_DEPENDS=		devel/desktop-file-utils \
			java/javaPathHelper

NO_TEST=		Yes

WRKDIST=		${WRKDIR}/idea-IC-191.6707.61
IJ=			${PREFIX}/intellij

# If NO_BUILD is set, JAVA_HOME doesn't get defined. So do
# a no-op for do-build.
do-build:
	@true

do-install:
	${INSTALL_DATA_DIR} ${IJ}
	cd ${WRKDIST} && pax -rw . ${IJ}
	@rm -rf ${IJ}/bin/libdbm64.so
	@rm -rf ${IJ}/jre
	@rm -rf ${IJ}/jre64
	@rm -rf ${IJ}/plugins/android
	@rm -rf ${IJ}/plugins/gradle/lib/native-platform-{freebsd,linux,osx,windows}*.jar
	@${SUBST_PROGRAM} ${FILESDIR}/idea ${PREFIX}/bin/idea
	@ln -s ${TRUEPREFIX}/bin/idea ${PREFIX}/bin/intellij
	${INSTALL_MAN} ${FILESDIR}/idea.1 ${PREFIX}/man/man1
	${INSTALL_DATA_DIR} ${PREFIX}/share/applications
	cd ${WRKDIST}/lib && ${JAVA_HOME}/bin/jar xf icons.jar
	${INSTALL_DATA} ${WRKDIST}/lib/icon.png ${IJ}/idea.png
	@${SUBST_DATA} ${FILESDIR}/intellij.desktop \
		${PREFIX}/share/applications/intellij.desktop

.include <bsd.port.mk>
