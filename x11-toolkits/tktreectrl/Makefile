PORTNAME=	tktreectrl
PORTVERSION=	2.4.1
CATEGORIES=	x11-toolkits tk
MASTER_SITES=	SF/tktreectrl/tktreectrl/tktreectrl-${PORTVERSION}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Multi-column hierarchical listbox widget
WWW=		https://tktreectrl.sourceforge.net/

LICENSE=	TclTk
LICENSE_NAME=	Tcl/Tk License
LICENSE_FILE=	${WRKSRC}/license.terms
LICENSE_PERMS=	dist-mirror dist-sell pkg-mirror pkg-sell auto-accept

USES=		tk:tea xorg
USE_LDCONFIG=	${PREFIX}/lib/${TCL_PKG}
USE_XORG=	x11

GNU_CONFIGURE_MANPREFIX=${PREFIX}/share
TCL_PKG=	treectrl${PORTVERSION}

.include <bsd.port.mk>
