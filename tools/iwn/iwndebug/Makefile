
MAN=

.include <bsd.compiler.mk>

.PATH:	${.CURDIR}/../../../../sys/dev/iwn/

CFLAGS+=-I${.CURDIR}/../../../../sys/dev/iwn/
CFLAGS+=-I${.CURDIR}/../../../../sys/
CFLAGS+=-DIWN_DEBUG

PROG=	iwndebug

BINDIR?=/usr/local/sbin

SRCS=	main.c

CFLAGS.clang+=	-fbracket-depth=512 -Wno-unused-function

.include <bsd.prog.mk>
