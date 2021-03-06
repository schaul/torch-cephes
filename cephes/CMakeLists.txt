# locate all cephes subfolders to process
FILE(GLOB src
    "bessel/*.c"
    "cmath/*.c"
    "cprob/*.c"
    "misc/*.c"
    "ellf/*.c"
    "polyn/*.c"
    )
# note: single/ is not compiled because it conflicts
# with many functions in cmath and cprob :(

# ignore files which have a main() 
LIST(REMOVE_ITEM src
    "${CMAKE_CURRENT_SOURCE_DIR}/cmath/mtst.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/cmath/dtestvec.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/cmath/mod2pi.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/ellf/ellf.c")

# ignore files who are exact duplicates of cmath
LIST(REMOVE_ITEM src
    "${CMAKE_CURRENT_SOURCE_DIR}/cprob/drand.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/cprob/const.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/cprob/mtherr.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/cprob/polevl.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/cprob/unity.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/misc/unity.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/misc/chbevl.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/misc/mtherr.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/misc/polevl.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/ellf/cmplx.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/ellf/const.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/ellf/mtherr.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/ellf/polevl.c"
    )

# ignore files in misc who are exact duplicates of any other
LIST(REMOVE_ITEM src
    "${CMAKE_CURRENT_SOURCE_DIR}/misc/psi.c"
    "${CMAKE_CURRENT_SOURCE_DIR}/misc/revers.c"
    )

# ignore rational polynomials of polyr.c,
# because it conflict with the simpler polynomials of polyn.c
LIST(REMOVE_ITEM src
    "${CMAKE_CURRENT_SOURCE_DIR}/polyn/polyr.c"
    )


SET(src "${src}" PARENT_SCOPE)
