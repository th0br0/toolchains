cc_toolchain_suite(
    name = "toolchain",
    # target_cpu | compiler
    toolchains = {
        "k8|gcc": ":bootlin-k8",
	"k8": ":bootlin-k8",
    },
)

filegroup(
    name = "linux_all_files",
    srcs = [
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:tool-wrappers",
        "@bootlin_x86_64_toolchain//:compiler_pieces",
    ],
)

filegroup(
    name = "linux_linker_files",
    srcs = [
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:ar",
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:gcc",
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:ld",
        "@bootlin_x86_64_toolchain//:compiler_pieces",
    ],
)

filegroup(
    name = "linux_compiler_files",
    srcs = [
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:as",
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:gcc",
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:ld",
    ],
)

# Here we'll keep things simple by including all files ditributed in archives.
filegroup(
    name = "all",
    srcs = glob(["**/*"]),
)

filegroup(
    name = "empty",
    srcs = [],
)

cc_toolchain(
    name = "bootlin-k8",
    all_files = ":linux_all_files",
    ar_files = "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:ar",
    as_files = "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:as",
    compiler_files = ":linux_compiler_files",
    cpu = "k8",
    dwp_files = ":empty",
    dynamic_runtime_libs = [":empty"],
    linker_files = ":linux_linker_files",
    objcopy_files = "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:objcopy",
    static_runtime_libs = [":empty"],
    strip_files = "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:strip",
    supports_param_files = 1,
    visibility = ["//visibility:public"],
)

toolchain(
    name = "cc_toolchain",
    exec_compatible_with = [
        "@bazel_tools//platforms:autoconfigured",
    ],
    target_compatible_with = [
    ],
    toolchain = ":bootlin-k8",
    toolchain_type = "@bazel_tools//tools/cpp:toolchain_type",
)

