# $OpenBSD: Makefile,v 1.12 2019/03/02 18:41:17 ajacoutot Exp $

COMMENT=	tiny download accelerator

V=		2.16.1
DISTNAME=	axel-$V

CATEGORIES=	net

HOMEPAGE=	https://github.com/axel-download-accelerator/axel

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes

MASTER_SITES=	https://github.com/axel-download-accelerator/axel/releases/download/v${V}/

WANTLIB=	c crypto iconv intl pthread ssl

LIB_DEPENDS=	devel/gettext

BUILD_DEPENDS=	devel/gettext-tools

USE_GMAKE=	Yes

CONFIGURE_STYLE=gnu
CONFIGURE_ENV=	CPPFLAGS=-I${LOCALBASE}/include \
		LDFLAGS=-L${LOCALBASE}/lib

pre-configure:
	@sed -i 's,/etc,${SYSCONFDIR},g' ${WRKSRC}/man/axel.1

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/axel
	${INSTALL_DATA} ${WRKSRC}/doc/axelrc.example \
		${PREFIX}/share/examples/axel/

.include <bsd.port.mk>
