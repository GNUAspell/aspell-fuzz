AUTOMAKE_OPTIONS = foreign nostdinc
ACLOCAL_AMFLAGS = -I m4

AM_CPPFLAGS = -I$(aspell_dir)/include
LDADD = $(aspell_dir)/lib/libaspell.a

if USE_OSSFUZZ_FLAG
FUZZ_FLAG = $(LIB_FUZZING_ENGINE)
else
if USE_OSSFUZZ_STATIC
LDADD += $(LIB_FUZZING_ENGINE)
FUZZ_FLAG =
else
LDADD += libstandaloneengine.a
FUZZ_FLAG =
endif
endif

noinst_PROGRAMS = \
	aspell_fuzzer
noinst_LIBRARIES = \
	libstandaloneengine.a

aspell_fuzzer_SOURCES = aspell_fuzzer.cpp
aspell_fuzzer_CXXFLAGS = $(AM_CXXFLAGS) $(FUZZ_FLAG)
aspell_fuzzer_LDFLAGS = $(AM_LDFLAGS) -static

libstandaloneengine_a_SOURCES = standaloneengine.cpp testinput.hpp
libstandaloneengine_a_CXXFLAGS = $(AM_CXXFLAGS)
