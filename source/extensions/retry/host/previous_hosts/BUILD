load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_extension",
    "envoy_cc_library",
    "envoy_extension_package",
)

licenses(["notice"])  # Apache 2

envoy_extension_package()

envoy_cc_library(
    name = "previous_hosts_predicate_lib",
    hdrs = ["previous_hosts.h"],
    deps = [
        "//include/envoy/upstream:retry_interface",
    ],
)

envoy_cc_extension(
    name = "config",
    srcs = ["config.cc"],
    hdrs = ["config.h"],
    category = "envoy.retry_host_predicates",
    security_posture = "robust_to_untrusted_downstream",
    deps = [
        ":previous_hosts_predicate_lib",
        "//include/envoy/registry",
        "//include/envoy/upstream:retry_interface",
        "@envoy_api//envoy/config/retry/previous_hosts/v2:pkg_cc_proto",
    ],
)
