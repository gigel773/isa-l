project(isa-l_tests)

set(SOURCES)

find_package(ZLIB REQUIRED)
include_directories(../../include ../../igzip ${ZLIB_INCLUDE_DIRS})

# Tests executables
add_executable(fuzz_inflate
        ../../tests/fuzz/igzip_fuzz_inflate.c
        ../../tests/fuzz/igzip_simple_inflate_fuzz_test.c)
add_executable(dump_inflate_corpus ../../tests/fuzz/igzip_dump_inflate_corpus.c)
add_executable(checked_inflate_fuzz
        ../../tests/fuzz/igzip_fuzz_inflate.c
        ../../tests/fuzz/igzip_checked_inflate_fuzz_test.c)

# Tests dependencies
target_link_libraries(fuzz_inflate isa-l)
target_link_libraries(dump_inflate_corpus isa-l)
target_link_libraries(checked_inflate_fuzz isa-l ${ZLIB_LIBRARIES})
