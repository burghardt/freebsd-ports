PORTNAME=	red-gandiva
PORTVERSION=	15.0.1
CATEGORIES=	databases rubygems
MASTER_SITES=	RG

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Ruby bindings of Gandiva
WWW=		https://arrow.apache.org/ \
		https://github.com/apache/arrow/tree/master/ruby/red-gandiva

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE.txt

BUILD_DEPENDS=	arrow>=${PORTVERSION}<${PORTVERSION:R}.2_99:databases/arrow \
		arrow-glib>=${PORTVERSION}<${PORTVERSION:R}.2_99:databases/arrow-glib \
		rubygem-rake>=0:devel/rubygem-rake
LIB_DEPENDS=	libarrow.so:databases/arrow \
		libarrow-glib.so:databases/arrow-glib
RUN_DEPENDS=	rubygem-red-arrow>=${PORTVERSION}<${PORTVERSION}_99:databases/rubygem-red-arrow

USES=		gem

NO_ARCH=	yes

.include <bsd.port.mk>
