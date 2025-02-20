PORTNAME=	duckdb
DISTVERSIONPREFIX=	v
DISTVERSION=	0.10.1
CATEGORIES=	databases

PATCH_SITES=	https://github.com/${GH_ACCOUNT}/${GH_PROJECT}/commit/
PATCHFILES+=	ca28b1954bbbb66d4d78221e3dd5f47e0b54dcca.patch:-p1 # check for IUTF8 flag defined before setting it: https://github.com/duckdb/duckdb/pull/11488

MAINTAINER=	yuri@FreeBSD.org
COMMENT=	In-process SQL OLAP database management system
WWW=		https://duckdb.org/

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		cmake:testing compiler:c++11-lang ssl
USE_GITHUB=	yes
GH_TUPLE=	duckdb:sqlite_scanner:c134346:sqlite/extension/sqlite_scanner

CMAKE_ON=	BUILD_SHARED_LIBS
CMAKE_OFF=	BUILD_UNITTESTS
CMAKE_ARGS=	-DOVERRIDE_GIT_DESCRIBE=v${DISTVERSION}-g00000000
CMAKE_TESTING_ON=	BUILD_UNITTESTS # 2 tests fail, see https://github.com/duckdb/duckdb/issues/10652
CMAKE_TESTING_TARGET=	${ALL_TARGET} # hack: works as empty target

BINARY_ALIAS=	git=false

OPTIONS_DEFINE=			TPCE
OPTIONS_DEFAULT=		TPCE
OPTIONS_GROUP=			EXTENSIONS
OPTIONS_GROUP_EXTENSIONS=	AUTOCOMPLETE EXCEL FTS HTTPFS ICU INET JEMALLOC JSON PARQUET SQLSMITH TPCDS TPCH \
				SQLITE_SCANNER

EXTENSIONS_DESC=		Extensions:

.for opt in ${OPTIONS_GROUP_EXTENSIONS}
.  if "${${opt}_BROKEN}" == ""
OPTIONS_DEFAULT+=	${opt}
.  endif
${opt}_DESC=		Build the ${opt} extension
DUCKDB_EXTENSIONS+=	;${opt:tl}
${opt}_PLIST_FILES=	lib/lib${opt:tl}_extension.a
.endfor

CMAKE_ARGS=	-DBUILD_EXTENSIONS="${DUCKDB_EXTENSIONS:tW:S/ //g:S/^;//}" \
		-DDUCKDB_MAJOR_VERSION=${PORTVERSION:R:R} \
		-DDUCKDB_MINOR_VERSION=${PORTVERSION:R:E} \
		-DDUCKDB_PATCH_VERSION=${PORTVERSION:E}

SQLITE_SCANNER_CXXFLAGS=	-I${WRKSRC}/extension/sqlite_scanner/src/include # workaround for the header not being found

TPCE_DESC=			Enable building of the TPC-E tool
TPCE_CMAKE_BOOL=		BUILD_TPCE

post-test: # run tests
	@cd ${TEST_WRKSRC} && test/unittest

.include <bsd.port.mk>
