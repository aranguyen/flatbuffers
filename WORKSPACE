workspace(name = "com_github_google_flatbuffers")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "platforms",
    sha256 = "379113459b0feaf6bfbb584a91874c065078aa673222846ac765f86661c27407",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/platforms/releases/download/0.0.5/platforms-0.0.5.tar.gz",
        "https://github.com/bazelbuild/platforms/releases/download/0.0.5/platforms-0.0.5.tar.gz",
    ],
)

http_archive(
    name = "build_bazel_rules_swift",
    sha256 = "a2fd565e527f83fb3f9eb07eb9737240e668c9242d3bc318712efa54a7deda97",
    url = "https://github.com/bazelbuild/rules_swift/releases/download/0.27.0/rules_swift.0.27.0.tar.gz",
)

load(
    "@build_bazel_rules_swift//swift:repositories.bzl",
    "swift_rules_dependencies",
)

swift_rules_dependencies()

load(
    "@build_bazel_rules_swift//swift:extras.bzl",
    "swift_rules_extra_dependencies",
)

swift_rules_extra_dependencies()

http_archive(
    name = "io_bazel_rules_go",
    sha256 = "16e9fca53ed6bd4ff4ad76facc9b7b651a89db1689a2877d6fd7b82aa824e366",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_go/releases/download/v0.34.0/rules_go-v0.34.0.zip",
        "https://github.com/bazelbuild/rules_go/releases/download/v0.34.0/rules_go-v0.34.0.zip",
    ],
)

load("@io_bazel_rules_go//go:deps.bzl", "go_rules_dependencies")

go_rules_dependencies()

##### Protobuf
_PROTOBUF_VERSION = "3.15.2"

http_archive(
    name = "com_google_protobuf",
    strip_prefix = "protobuf-" + _PROTOBUF_VERSION,
    urls = [
        "https://github.com/protocolbuffers/protobuf/archive/v" + _PROTOBUF_VERSION + ".tar.gz",
    ],
)

##### GRPC
_GRPC_VERSION = "1.49.0"  # https://github.com/grpc/grpc/releases/tag/v1.49.0

http_archive(
    name = "com_github_grpc_grpc",
    strip_prefix = "grpc-" + _GRPC_VERSION,
    urls = ["https://github.com/grpc/grpc/archive/refs/tags/v" + _GRPC_VERSION + ".tar.gz"],
)

load("@com_github_grpc_grpc//bazel:grpc_deps.bzl", "grpc_deps")

grpc_deps()

load("@com_github_grpc_grpc//bazel:grpc_extra_deps.bzl", "grpc_extra_deps")

grpc_extra_deps()

# rules_go from https://github.com/bazelbuild/rules_go/releases/tag/v0.34.0
http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "965ee2492a2b087cf9e0f2ca472aeaf1be2eb650e0cfbddf514b9a7d3ea4b02a",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/5.2.0/rules_nodejs-5.2.0.tar.gz"],
)

load("@build_bazel_rules_nodejs//:repositories.bzl", "build_bazel_rules_nodejs_dependencies")

build_bazel_rules_nodejs_dependencies()

load("@build_bazel_rules_nodejs//:index.bzl", "node_repositories", "yarn_install")

node_repositories()

yarn_install(
    name = "npm",
    exports_directories_only = False,
    # Unfreeze to add/remove packages.
    frozen_lockfile = True,
    package_json = "//:package.json",
    symlink_node_modules = False,
    yarn_lock = "//:yarn.lock",
)
