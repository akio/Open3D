package(default_visibility = ["//visibility:public"])

cc_library(
    name = "jsoncpp",
    hdrs = ["json_tool.h", "json_valueiterator.inl"] + glob(["include/json/*.h"]),
    srcs = glob(["*.cpp"]),
    includes = ["include", "."],
    linkstatic = True,
)
