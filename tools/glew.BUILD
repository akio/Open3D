package(default_visibility = ["//visibility:public"])

cc_library(
    name = "glew",
    hdrs = glob(["include/GL/*.h"]),
    srcs = glob([
        "src/glew.c",
    ]),
    includes = ["include"],
    copts = ["-D_GLFW_X11"],
    linkstatic = False,
)
