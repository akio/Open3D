package(default_visibility = ["//visibility:public"])

cc_library(
    name = "pybind11",
    hdrs = glob([
        "include/pybind11/*.h",
        "include/pybind11/detail/*.h",
    ]),
    includes = [
			"include",
		],
		deps = [
			"@python",
		]
)

