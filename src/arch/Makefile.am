AM_CPPFLAGS += -I$(top_srcdir)/src/ccstruct -I$(top_srcdir)/src/ccutil -I$(top_srcdir)/src/viewer

SUBDIRS =
AM_CXXFLAGS =

if VISIBILITY
AM_CXXFLAGS += -fvisibility=hidden -fvisibility-inlines-hidden
AM_CPPFLAGS += -DTESS_EXPORTS
endif

pkginclude_HEADERS =

noinst_HEADERS = dotproduct.h dotproductavx.h dotproductsse.h
noinst_HEADERS += intsimdmatrix.h intsimdmatrixavx2.h intsimdmatrixsse.h
noinst_HEADERS += simddetect.h

noinst_LTLIBRARIES = libtesseract_native.la
noinst_LTLIBRARIES += libtesseract_avx.la libtesseract_avx2.la
noinst_LTLIBRARIES += libtesseract_sse.la
noinst_LTLIBRARIES += libtesseract_arch.la

libtesseract_arch_la_CPPFLAGS = $(AM_CPPFLAGS)
if AVX_OPT
libtesseract_arch_la_CPPFLAGS += -DAVX
libtesseract_avx_la_CXXFLAGS = -ffast-math -mavx
endif
if AVX2_OPT
libtesseract_arch_la_CPPFLAGS += -DAVX2
libtesseract_avx2_la_CXXFLAGS = -ffast-math -mavx2
endif
if SSE41_OPT
libtesseract_arch_la_CPPFLAGS += -DSSE4_1
libtesseract_sse_la_CXXFLAGS = -ffast-math -msse4.1
endif

libtesseract_native_la_CXXFLAGS = -O3 -ffast-math
if MARCH_NATIVE_OPT
libtesseract_native_la_CXXFLAGS += -march=native -mtune=native
endif
libtesseract_native_la_SOURCES = dotproduct.cpp

libtesseract_arch_la_SOURCES = intsimdmatrix.cpp simddetect.cpp

libtesseract_avx_la_SOURCES = dotproductavx.cpp

libtesseract_avx2_la_SOURCES = intsimdmatrixavx2.cpp

libtesseract_sse_la_SOURCES = dotproductsse.cpp intsimdmatrixsse.cpp
