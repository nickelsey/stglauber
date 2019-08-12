# get source files for libstglauber
file(GLOB tmp *.cxx)
set(STGLAUBER_SRCS ${STGLAUBER_SRCS} ${tmp})

# get header files for libstglauber
file(GLOB tmp *.h)
set(STGLAUBER_HEADERS ${tmp})

# get test source files
file(GLOB tmp *_test.cxx)
set(SCT_TEST_SRCS ${SCT_TEST_SRCS} ${tmp})

# and exclude the test files from libstglauber
if(SCT_TEST_SRCS)
  list(REMOVE_ITEM STGLAUBER_SRCS ${SCT_TEST_SRCS})
endif(SCT_TEST_SRCS)

# get test benchmark files
file(GLOB tmp *_benchmark.cxx)
set(SCT_BENCH_SRCS ${SCT_BENCH_SRCS} ${tmp})

# and exclude the benchmark files from libstglauber
if(SCT_BENCH_SRCS)
  list(REMOVE_ITEM STGLAUBER_SRCS ${SCT_BENCH_SRCS})
endif(SCT_BENCH_SRCS)

# install headers
install(FILES ${STGLAUBER_HEADERS} DESTINATION include/stglauber/StFastGlauberMcMaker)



# export file lists to parent scope
set(STGLAUBER_SRCS ${STGLAUBER_SRCS} PARENT_SCOPE)
set(SCT_TEST_SRCS ${SCT_TEST_SRCS} PARENT_SCOPE)
set(SCT_BENCH_SRCS ${SCT_BENCH_SRCS} PARENT_SCOPE)
