PORTNAME=	jove
PORTVERSION=	4.17.5.3
CATEGORIES=	editors
MASTER_SITES=	https://github.com/jonmacs/jove/releases/download/${PORTVERSION}/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Jonathan's Own Version of Emacs
WWW=		https://github.com/jonmacs/jove

LICENSE=	JOVE
LICENSE_NAME=	JOVE License
LICENSE_FILE=	${WRKSRC}/LICENSE
LICENSE_PERMS=	dist-mirror dist-sell pkg-mirror pkg-sell auto-accept

USES=		ncurses

EXTRACT_SUFX=	.tgz

MAKE_ARGS=	LIBS="${LDFLAGS} -lncurses"

OPTIONS_DEFINE=	EXTRADOCS
OPTIONS_DEFAULT=
OPTIONS_SUB=	yes

EXTRADOCS_DESC=	Build and install cmds.doc
EXTRADOCS_USES=	groff

post-patch:
# Fix collisions with getline(3)
	@${REINPLACE_CMD} 's|[[:<:]]getline[[:>:]]|get_line|g' ${WRKSRC}/*.c ${WRKSRC}/*.h

post-patch-EXTRADOCS-off:
	@${REINPLACE_CMD} -E 's|^(all:.*) doc/cmds\.doc$$|\1|' ${WRKSRC}/Makefile
	@${REINPLACE_CMD} 's|^CMDS.DOC = .*|CMDS.DOC=|' ${WRKSRC}/Makefile

.include <bsd.port.mk>
