workspace(
  name = "examples_program",
  managed_directories = {"@npm": ["node_modules"]},
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "3b0116a8a91a75678a57ba676c246ac0fa9c90dc3d46daef305b11b54ed4467e",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/0.33.1/rules_nodejs-0.33.1.tar.gz"],
)
load("@build_bazel_rules_nodejs//:defs.bzl", "node_repositories", "yarn_install")

node_repositories(
    # https://github.com/bazelbuild/rules_nodejs/blob/master/internal/node/node_repositories.bzl
    node_repositories = {
        "11.15.0-darwin_amd64": ("node-v11.15.0-darwin-x64.tar.gz", "node-v11.15.0-darwin-x64", "e953b657b1049e1de509a3fd0700cfeecd175f75a0d141d71393aa0d71fa29a9"),
        "11.15.0-linux_amd64": ("node-v11.15.0-linux-x64.tar.xz", "node-v11.15.0-linux-x64", "17424aef198fa322b93c79217ce7e8cdd264fed40383abbbd3e63c305ce1d7d8"),
        "11.15.0-windows_amd64": ("node-v11.15.0-win-x64.zip", "node-v11.15.0-win-x64", "f3cef50acf566724a5ec5df7697fb527d7339cafdae6c7c406a39358aee6cdf8"),

    },
    node_version = "11.15.0",
    node_urls = ["https://nodejs.org/dist/v{version}/{filename}"],
    yarn_repositories = {
        "1.16.0": ("yarn-v1.16.0.tar.gz", "yarn-v1.16.0", "df202627d9a70cf09ef2fb11cb298cb619db1b958590959d6f6e571b50656029"),
    },
    yarn_version = "1.16.0",
    yarn_urls = ["https://github.com/yarnpkg/yarn/releases/download/v{version}/{filename}"],
    package_json = ["//:package.json"]
)

yarn_install(
    name = "npm",
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
    always_hide_bazel_files = True,
)
