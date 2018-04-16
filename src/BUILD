package(default_visibility = ["//visibility:public"])

cc_library(
   name = 'Core',
   hdrs = [
       'Core/Core.h',
   ] + glob([
    "Core/Camera/*.h",
    "Core/Geometry/*.h",
    "Core/Integration/*.h",
    "Core/Odometry/*.h",
    "Core/Registration/*.h",
    "Core/Utility/*.h",
   ]),
   srcs = glob([
    "Core/Camera/*.cpp",
    "Core/Geometry/*.cpp",
    "Core/Integration/*.cpp",
    "Core/Odometry/*.cpp",
    "Core/Registration/*.cpp",
    "Core/Utility/*.cpp",
   ]),
   includes = [
     ".",
   ],
   deps = [
    "IO",
    "@eigen",
    "@jsoncpp",
    "@flann",
   ],
   linkstatic = False,
)

cc_library(
   name = "IO",
   hdrs = [
       'IO/IO.h',
   ] + glob([
    "IO/ClassIO/*.h",
    "IO/FileFormat/*.h",
    "Core/Camera/*.h",
    "Core/Geometry/*.h",
    "Core/Utility/*.h",
    "Core/Registration/*.h",
    "External/liblzf/lzf.h",
   ]),
   srcs = glob([
    "IO/ClassIO/*.cpp",
    "IO/FileFormat/*.cpp",
   ]),
   includes = [
     ".",
   ],
   deps = [
    "@eigen",
    "@jsoncpp",
    "@rply",
    "@liblzf",
    "@libpng",
    "@libjpeg",
    "@zlib",
   ],
   linkstatic = False,
)

genrule(
    name = "gen_shader",
    srcs = [
        "Visualization/Shader/GLSL/ImageFragmentShader.glsl",
        "Visualization/Shader/GLSL/ImageMaskFragmentShader.glsl",
        "Visualization/Shader/GLSL/ImageMaskVertexShader.glsl",
        "Visualization/Shader/GLSL/ImageVertexShader.glsl",
        "Visualization/Shader/GLSL/NormalFragmentShader.glsl",
        "Visualization/Shader/GLSL/NormalVertexShader.glsl",
        "Visualization/Shader/GLSL/PhongFragmentShader.glsl",
        "Visualization/Shader/GLSL/PhongVertexShader.glsl",
        "Visualization/Shader/GLSL/PickingFragmentShader.glsl",
        "Visualization/Shader/GLSL/PickingVertexShader.glsl",
        "Visualization/Shader/GLSL/Simple2DFragmentShader.glsl",
        "Visualization/Shader/GLSL/Simple2DVertexShader.glsl",
        "Visualization/Shader/GLSL/SimpleBlackFragmentShader.glsl",
        "Visualization/Shader/GLSL/SimpleBlackVertexShader.glsl",
        "Visualization/Shader/GLSL/SimpleFragmentShader.glsl",
        "Visualization/Shader/GLSL/SimpleVertexShader.glsl",
    ],
    outs = ["Visualization/Shader/Shader.h"],
    tools = ["EncodeShader"],
    cmd = (
        "$(location EncodeShader) $@"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/ImageFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/ImageMaskFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/ImageMaskVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/ImageVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/NormalFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/NormalVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/PhongFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/PhongVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/PickingFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/PickingVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/Simple2DFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/Simple2DVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/SimpleBlackFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/SimpleBlackVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/SimpleFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location Visualization/Shader/GLSL/SimpleVertexShader.glsl)"
    ),
)


cc_library(
   name = "Visualization",
   hdrs = [
       "Visualization/Visualization.h",
       "Visualization/Shader/Shader.h",
       "External/tinyfiledialogs/tinyfiledialogs.h",
   ] + glob([
     "Visualization/Utility/*.h",
     "Visualization/Shader/*.h",
     "Visualization/Visualizer/*.h",
     "Core/Geometry/*.h",
     "Core/Utility/*.h",
     "Core/Camera/*.h",
     "IO/ClassIO/*.h",
   ]),
   srcs = glob([
     "Visualization/Utility/*.cpp",
     "Visualization/Shader/*.cpp",
     "Visualization/Visualizer/*.cpp",
   ]),
   includes = [
     ".",
   ],
   data = glob(["Visualization/Shader/GLSL/*.glsl"]),
   deps = [
     "Core",
     "@eigen",
     "@jsoncpp",
     "@tinyfiledialogs",
     "@glfw",
     "@glew",
   ],
   linkstatic = False,
)

cc_library(
    name = "_ManuallyAlignPointCloud",
    hdrs = glob(["Tools/ManuallyAlignPointCloud/*.h"]),
)

cc_binary(
    name = "ManuallyAlignPointCloud",
    srcs = glob(["Tools/ManuallyAlignPointCloud/*.cpp"]),
    deps = [
        "IO",
        "Core",
        "Visualization",
        "_ManuallyAlignPointCloud",
    ],
)

cc_binary(
    name = "EncodeShader",
    srcs = ["Tools/EncodeShader.cpp"],
)

cc_binary(
    name = "MergeMesh",
    srcs = ["Tools/MergeMesh.cpp"],
    deps = ["IO","Core"],
)

cc_binary(
    name = "ConvertPointCloud",
    srcs = [
        "Tools/ConvertPointCloud.cpp"
    ],
    deps = [
        "IO",
        "Core",
        "@jsoncpp",
        "@libpng",
        "@libjpeg",
        "@zlib",
    ],
)

cc_binary(
    name = "ManuallyCropPointCloud",
    srcs = ["Tools/ManuallyCropPointCloud.cpp"],
    deps = ["Visualization", "IO","Core"],
)

cc_binary(
    name = "ViewGeometry",
    srcs = ["Tools/ViewGeometry.cpp"],
    deps = [
        "Visualization",
        "IO",
        "Core",
        "@jsoncpp",
    ],
)

cc_library(
    name = "_py3d",
    hdrs = glob([
        "Python/*.h",
        "Python/Core/*.h",
        "Python/IO/*.h",
        "Python/Visualization/*.h",
    ]),
)

cc_binary(
    name = "py3d",
    srcs = glob([
            "Python/*.cpp",
            "Python/Core/*.cpp",
            "Python/IO/*.cpp",
            "Python/Visualization/*.cpp",
    ]),
    includes = [
      "Python",
      "Python/Core",
      "Python/IO",
      "Python/Visualization",
    ],
    deps = [
        "_py3d",
        "Core",
        "IO",
        "Visualization",
        "@pybind11",
    ],
)


cc_test(
    name = "TestPointCloud",
    srcs = ["Test/TestPointCloud.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
    args = ["src/Test/TestData/fragment.pcd"],
    timeout = 'long',
)

cc_test(
    name = "TestCameraPoseTrajectory",
    srcs = ["Test/TestCameraPoseTrajectory.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestLineSet",
    srcs = ["Test/TestLineSet.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestTriangleMesh",
    srcs = ["Test/TestTriangleMesh.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestVisualizer",
    srcs = ["Test/TestVisualizer.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestOpenMP",
    srcs = ["Test/TestOpenMP.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestFlann",
    srcs = ["Test/TestFlann.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestFileSystem",
    srcs = ["Test/TestFileSystem.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestProgramOptions",
    srcs = ["Test/TestProgramOptions.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestDepthCapture",
    srcs = ["Test/TestDepthCapture.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestPCDFileFormat",
    srcs = ["Test/TestPCDFileFormat.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestFileDialog",
    srcs = ["Test/TestFileDialog.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

#cc_test(
#    name = "TestRealSense",
#    srcs = ["Test/TestRealSense.cpp"],
#    deps = ["Core", "IO", "Visualization"],
#    data = ["Test/TestData"],
#)

cc_test(
    name = "TestImage",
    srcs = ["Test/TestImage.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestPoseGraph",
    srcs = ["Test/TestPoseGraph.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)

cc_test(
    name = "TestRegistrationRANSAC",
    srcs = ["Test/TestRegistrationRANSAC.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["Test/TestData"],
)
