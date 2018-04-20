package(default_visibility = ["//visibility:public"])

cc_library(
   name = 'Core',
   hdrs = [
     'src/Core/Core.h',
   ] + glob([
     "src/Core/Camera/*.h",
     "src/Core/Geometry/*.h",
     "src/Core/Integration/*.h",
     "src/Core/Odometry/*.h",
     "src/Core/Registration/*.h",
     "src/Core/Utility/*.h",
   ]),
   srcs = glob([
     "src/Core/Camera/*.cpp",
     "src/Core/Geometry/*.cpp",
     "src/Core/Integration/*.cpp",
     "src/Core/Odometry/*.cpp",
     "src/Core/Registration/*.cpp",
     "src/Core/Utility/*.cpp",
   ]),
   includes = [
     "src",
   ],
   deps = [
     "IO",
     "//src/External/Eigen:eigen",
     "//src/External/jsoncpp",
     "//src/External/flann",
   ],
   linkstatic = False,
)

cc_library(
   name = "IO",
   hdrs = [
     "src/IO/IO.h",
   ] + glob([
     "src/IO/ClassIO/*.h",
     "src/IO/FileFormat/*.h",
     "src/Core/Camera/*.h",
     "src/Core/Geometry/*.h",
     "src/Core/Utility/*.h",
     "src/Core/Registration/*.h",
     "src/External/liblzf/lzf.h",
   ]),
   srcs = glob([
     "src/IO/ClassIO/*.cpp",
     "src/IO/FileFormat/*.cpp",
   ]),
   includes = [
     "src",
   ],
   deps = [
     "//src/External/Eigen:eigen",
     "//src/External/jsoncpp",
     "//src/External/rply",
     "//src/External/liblzf",
     "//src/External/libpng",
     "//src/External/libjpeg",
     "//src/External/zlib",
   ],
   linkstatic = False,
)

genrule(
    name = "gen_shader",
    srcs = [
        "src/Visualization/Shader/GLSL/ImageFragmentShader.glsl",
        "src/Visualization/Shader/GLSL/ImageMaskFragmentShader.glsl",
        "src/Visualization/Shader/GLSL/ImageMaskVertexShader.glsl",
        "src/Visualization/Shader/GLSL/ImageVertexShader.glsl",
        "src/Visualization/Shader/GLSL/NormalFragmentShader.glsl",
        "src/Visualization/Shader/GLSL/NormalVertexShader.glsl",
        "src/Visualization/Shader/GLSL/PhongFragmentShader.glsl",
        "src/Visualization/Shader/GLSL/PhongVertexShader.glsl",
        "src/Visualization/Shader/GLSL/PickingFragmentShader.glsl",
        "src/Visualization/Shader/GLSL/PickingVertexShader.glsl",
        "src/Visualization/Shader/GLSL/Simple2DFragmentShader.glsl",
        "src/Visualization/Shader/GLSL/Simple2DVertexShader.glsl",
        "src/Visualization/Shader/GLSL/SimpleBlackFragmentShader.glsl",
        "src/Visualization/Shader/GLSL/SimpleBlackVertexShader.glsl",
        "src/Visualization/Shader/GLSL/SimpleFragmentShader.glsl",
        "src/Visualization/Shader/GLSL/SimpleVertexShader.glsl",
    ],
    outs = ["src/Visualization/Shader/Shader.h"],
    tools = ["EncodeShader"],
    cmd = (
        "$(location EncodeShader) $@"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/ImageFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/ImageMaskFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/ImageMaskVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/ImageVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/NormalFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/NormalVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/PhongFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/PhongVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/PickingFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/PickingVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/Simple2DFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/Simple2DVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/SimpleBlackFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/SimpleBlackVertexShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/SimpleFragmentShader.glsl)"
        + " && $(location EncodeShader) $@ $(location src/Visualization/Shader/GLSL/SimpleVertexShader.glsl)"
    ),
)


cc_library(
   name = "Visualization",
   hdrs = [
     "src/Visualization/Visualization.h",
     "src/Visualization/Shader/Shader.h",
   ] + glob([
     "src/Visualization/Utility/*.h",
     "src/Visualization/Shader/*.h",
     "src/Visualization/Visualizer/*.h",
     "src/Core/Geometry/*.h",
     "src/Core/Utility/*.h",
     "src/Core/Camera/*.h",
     "src/IO/ClassIO/*.h",
   ]),
   srcs = glob([
     "src/Visualization/Utility/*.cpp",
     "src/Visualization/Shader/*.cpp",
     "src/Visualization/Visualizer/*.cpp",
   ]),
   includes = [
     "src",
   ],
   data = glob(["src/isualization/Shader/GLSL/*.glsl"]),
   deps = [
     "Core",
     "//src/External/Eigen:eigen",
     "//src/External/jsoncpp",
     "//src/External/tinyfiledialogs",
     "//src/External/GLFW:glfw",
     "//src/External/glew",
   ],
   linkstatic = False,
)

cc_library(
    name = "_ManuallyAlignPointCloud",
    hdrs = glob(["src/Tools/ManuallyAlignPointCloud/*.h"]),
)

cc_binary(
    name = "ManuallyAlignPointCloud",
    srcs = glob(["src/Tools/ManuallyAlignPointCloud/*.cpp"]),
    deps = [
        "IO",
        "Core",
        "Visualization",
        "_ManuallyAlignPointCloud",
    ],
)

cc_binary(
    name = "EncodeShader",
    srcs = ["src/Tools/EncodeShader.cpp"],
)

cc_binary(
    name = "MergeMesh",
    srcs = ["src/Tools/MergeMesh.cpp"],
    deps = ["IO","Core"],
)

cc_binary(
    name = "ConvertPointCloud",
    srcs = [
        "src/Tools/ConvertPointCloud.cpp"
    ],
    deps = [
        "IO",
        "Core",
        "//src/External/jsoncpp",
        "//src/External/libpng",
        "//src/External/libjpeg",
        "//src/External/zlib",
    ],
)

cc_binary(
    name = "ManuallyCropPointCloud",
    srcs = ["src/Tools/ManuallyCropPointCloud.cpp"],
    deps = ["Visualization", "IO","Core"],
)

cc_binary(
    name = "ViewGeometry",
    srcs = ["src/Tools/ViewGeometry.cpp"],
    deps = [
        "Visualization",
        "IO",
        "Core",
        "//src/External/jsoncpp",
    ],
)

cc_library(
    name = "_py3d",
    hdrs = glob([
        "src/Python/*.h",
        "src/Python/Core/*.h",
        "src/Python/IO/*.h",
        "src/Python/Visualization/*.h",
    ]),
)

cc_binary(
    name = "py3d",
    srcs = glob([
      "src/Python/*.cpp",
      "src/Python/Core/*.cpp",
      "src/Python/IO/*.cpp",
      "src/Python/Visualization/*.cpp",
    ]),
    includes = [
      "src/Python",
      "src/Python/Core",
      "src/Python/IO",
      "src/Python/Visualization",
    ],
    deps = [
        "_py3d",
        "Core",
        "IO",
        "Visualization",
        "//src/External/pybind11",
    ],
)


cc_test(
    name = "TestPointCloud",
    srcs = ["src/Test/TestPointCloud.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
    args = ["src/Test/TestData/fragment.pcd"],
    timeout = 'long',
)

cc_test(
    name = "TestCameraPoseTrajectory",
    srcs = ["src/Test/TestCameraPoseTrajectory.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestLineSet",
    srcs = ["src/Test/TestLineSet.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestTriangleMesh",
    srcs = ["src/Test/TestTriangleMesh.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestVisualizer",
    srcs = ["src/Test/TestVisualizer.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestOpenMP",
    srcs = ["src/Test/TestOpenMP.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestFlann",
    srcs = ["src/Test/TestFlann.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestFileSystem",
    srcs = ["src/Test/TestFileSystem.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestProgramOptions",
    srcs = ["src/Test/TestProgramOptions.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestDepthCapture",
    srcs = ["src/Test/TestDepthCapture.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestPCDFileFormat",
    srcs = ["src/Test/TestPCDFileFormat.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestFileDialog",
    srcs = ["src/Test/TestFileDialog.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

#cc_test(
#    name = "TestRealSense",
#    srcs = ["src/Test/TestRealSense.cpp"],
#    deps = ["Core", "IO", "Visualization"],
#    data = ["src/Test/TestData"],
#)

cc_test(
    name = "TestImage",
    srcs = ["src/Test/TestImage.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestPoseGraph",
    srcs = ["src/Test/TestPoseGraph.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)

cc_test(
    name = "TestRegistrationRANSAC",
    srcs = ["src/Test/TestRegistrationRANSAC.cpp"],
    deps = ["Core", "IO", "Visualization"],
    data = ["src/Test/TestData"],
)
