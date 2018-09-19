project(isa-l_library C ASM)

enable_language(ASM_NASM)

include_directories(../../include ../../igzip)

set(C_SOURCES
        ../../igzip/igzip.c
        ../../igzip/hufftables_c.c
        ../../igzip/igzip_base.c
        ../../igzip/igzip_icf_base.c
        ../../igzip/crc32_gzip_base.c
        ../../igzip/flatten_ll.c
        ../../igzip/encode_df.c
        ../../igzip/igzip_icf_body.c
        ../../igzip/igzip_base_aliases.c
        ../../igzip/proc_heap_base.c
        ../../igzip/igzip_inflate.c
        ../../igzip/huff_codes.c
        )

set(ASM_SOURCES
        ../../igzip/igzip_body.asm
        ../../igzip/igzip_finish.asm
        ../../igzip/igzip_icf_body_h1_gr_bt.asm
        ../../igzip/igzip_icf_finish.asm
        ../../igzip/rfc1951_lookup.asm
        ../../igzip/crc32_gzip.asm
        ../../igzip/adler32_sse.asm
        ../../igzip/adler32_avx2_4.asm
        ../../igzip/igzip_multibinary.asm
        ../../igzip/igzip_update_histogram_01.asm
        ../../igzip/igzip_update_histogram_04.asm
        ../../igzip/igzip_decode_block_stateless_01.asm
        ../../igzip/igzip_decode_block_stateless_04.asm
        ../../igzip/igzip_inflate_multibinary.asm
        ../../igzip/encode_df_04.asm
        ../../igzip/encode_df_06.asm
        ../../igzip/proc_heap.asm
        ../../igzip/igzip_deflate_hash.asm
        ../../igzip/igzip_gen_icf_map_lh1_06.asm
        ../../igzip/igzip_gen_icf_map_lh1_04.asm
        ../../igzip/igzip_set_long_icf_fg_04.asm
        ../../igzip/igzip_set_long_icf_fg_06.asm)

set_source_files_properties(${ASM_SOURCES} PROPERTIES COMPILE_FLAGS
        "-I${CMAKE_CURRENT_SOURCE_DIR}/../../igzip/ -I${CMAKE_CURRENT_SOURCE_DIR}/../../include/")

add_library(isa-l ${C_SOURCES} ${ASM_SOURCES})
