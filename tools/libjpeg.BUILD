package(default_visibility = ["//visibility:public"])

cc_library(
    name = "libjpeg",
    hdrs = glob(["*.h"]),
    srcs = glob(["*.c"], exclude=["jmemnobs.c"]),
    includes = ["."],
    linkstatic = False,
)

