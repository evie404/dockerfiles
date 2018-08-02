load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_file")

git_repository(
    name = "io_bazel_rules_docker",
    commit = "c7a93454d27e09ef707dfca53887ed0ff4372f04",
    remote = "https://github.com/bazelbuild/rules_docker.git",
)

git_repository(
    name = "io_bazel_rules_k8s",
    commit = "8c615639dbb4592f4a471fc22f19c84f8fc35569",
    remote = "https://github.com/bazelbuild/rules_k8s.git",
)

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_pull",
    container_repositories = "repositories",
)

# This is NOT needed when going through the language lang_image
# "repositories" function(s).
container_repositories()

container_pull(
  name = "alphine_base",
  registry = "registry.hub.docker.com",
  repository = "library/alpine",
  # 'tag' is also supported, but digest is encouraged for reproducibility.
  digest = "sha256:7043076348bf5040220df6ad703798fd8593a0918d06d3ce30c6c93be117e430",
  tag = "3.8",
)

http_archive(
    name = "glider-v0.6.3",
    urls = ["https://github.com/nadoo/glider/releases/download/v0.6.3/glider-v0.6.3-linux-amd64.zip"],
    sha256 = "2675e2396f85db51618a45cd203e286ebc860ce0a900c87f169281725412ef0b",
    build_file_content = """
filegroup(
    name = "glider-src",
    srcs = ["glider"],
    visibility = ["//visibility:public"]
)
    """,
)
