load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_mock",
    "envoy_cc_test",
    "envoy_package",
)
load(
    "//test/extensions:extensions_build_system.bzl",
    "envoy_extension_cc_test",
)

licenses(["notice"])  # Apache 2

envoy_package()

envoy_extension_cc_test(
    name = "redis_cluster_test",
    srcs = ["redis_cluster_test.cc"],
    extension_names = ["envoy.clusters.redis"],
    rbe_pool = "6gig",
    deps = [
        "//source/common/event:dispatcher_lib",
        "//source/common/network:utility_lib",
        "//source/common/upstream:upstream_lib",
        "//source/extensions/clusters/redis:redis_cluster",
        "//source/extensions/clusters/redis:redis_cluster_lb",
        "//source/extensions/filters/network/redis_proxy:config",
        "//source/extensions/load_balancing_policies/cluster_provided:config",
        "//source/extensions/load_balancing_policies/round_robin:config",
        "//source/extensions/transport_sockets/raw_buffer:config",
        "//source/server:transport_socket_config_lib",
        "//test/common/upstream:utility_lib",
        "//test/extensions/clusters/redis:redis_cluster_mocks",
        "//test/extensions/filters/network/common/redis:redis_mocks",
        "//test/extensions/filters/network/common/redis:test_utils_lib",
        "//test/extensions/filters/network/redis_proxy:redis_mocks",
        "//test/mocks:common_lib",
        "//test/mocks/local_info:local_info_mocks",
        "//test/mocks/network:network_mocks",
        "//test/mocks/protobuf:protobuf_mocks",
        "//test/mocks/runtime:runtime_mocks",
        "//test/mocks/server:admin_mocks",
        "//test/mocks/server:instance_mocks",
        "//test/mocks/ssl:ssl_mocks",
        "//test/mocks/thread_local:thread_local_mocks",
        "//test/mocks/upstream:cluster_info_mocks",
        "//test/mocks/upstream:cluster_manager_mocks",
        "//test/mocks/upstream:health_check_event_logger_mocks",
        "//test/mocks/upstream:health_checker_mocks",
        "//test/mocks/upstream:priority_set_mocks",
        "//test/test_common:utility_lib",
        "@envoy_api//envoy/config/cluster/v3:pkg_cc_proto",
        "@envoy_api//envoy/extensions/clusters/redis/v3:pkg_cc_proto",
        "@envoy_api//envoy/extensions/filters/network/redis_proxy/v3:pkg_cc_proto",
    ],
)

envoy_extension_cc_test(
    name = "redis_cluster_lb_test",
    srcs = ["redis_cluster_lb_test.cc"],
    extension_names = ["envoy.clusters.redis"],
    rbe_pool = "6gig",
    deps = [
        "//envoy/upstream:cluster_manager_interface",
        "//source/common/event:dispatcher_lib",
        "//source/common/network:utility_lib",
        "//source/common/upstream:cluster_factory_lib",
        "//source/common/upstream:upstream_lib",
        "//source/extensions/clusters/redis:redis_cluster",
        "//source/extensions/clusters/redis:redis_cluster_lb",
        "//source/extensions/filters/network/common/redis:client_interface",
        "//source/extensions/filters/network/common/redis:codec_lib",
        "//source/extensions/filters/network/common/redis:supported_commands_lib",
        "//source/extensions/load_balancing_policies/cluster_provided:config",
        "//source/extensions/transport_sockets/raw_buffer:config",
        "//source/server:transport_socket_config_lib",
        "//test/common/upstream:utility_lib",
        "//test/extensions/clusters/redis:redis_cluster_mocks",
        "//test/extensions/filters/network/common/redis:redis_mocks",
        "//test/extensions/filters/network/common/redis:test_utils_lib",
        "//test/extensions/filters/network/redis_proxy:redis_mocks",
        "//test/mocks:common_lib",
        "//test/mocks/local_info:local_info_mocks",
        "//test/mocks/network:network_mocks",
        "//test/mocks/protobuf:protobuf_mocks",
        "//test/mocks/runtime:runtime_mocks",
        "//test/mocks/server:server_mocks",
        "//test/mocks/ssl:ssl_mocks",
        "//test/mocks/thread_local:thread_local_mocks",
        "//test/mocks/upstream:cluster_info_mocks",
        "//test/test_common:simulated_time_system_lib",
        "//test/test_common:utility_lib",
    ],
)

envoy_extension_cc_test(
    name = "redis_cluster_integration_test",
    size = "large",
    srcs = ["redis_cluster_integration_test.cc"],
    extension_names = ["envoy.clusters.redis"],
    rbe_pool = "6gig",
    deps = [
        "//source/extensions/clusters/redis:redis_cluster",
        "//source/extensions/clusters/redis:redis_cluster_lb",
        "//source/extensions/filters/network/redis_proxy:config",
        "//source/extensions/load_balancing_policies/cluster_provided:config",
        "//source/extensions/load_balancing_policies/round_robin:config",
        "//test/integration:ads_integration_lib",
        "//test/integration:integration_lib",
        "@envoy_api//envoy/config/bootstrap/v3:pkg_cc_proto",
    ],
)

envoy_cc_mock(
    name = "redis_cluster_mocks",
    srcs = ["mocks.cc"],
    hdrs = ["mocks.h"],
    deps = [
        "//envoy/upstream:upstream_interface",
        "//source/common/upstream:cluster_factory_lib",
        "//source/common/upstream:upstream_lib",
        "//source/extensions/clusters/redis:redis_cluster",
        "@envoy_api//envoy/extensions/clusters/redis/v3:pkg_cc_proto",
        "@envoy_api//envoy/extensions/filters/network/redis_proxy/v3:pkg_cc_proto",
    ],
)

envoy_cc_test(
    name = "crc16_test",
    srcs = ["crc16_test.cc"],
    rbe_pool = "6gig",
    deps = ["//source/extensions/clusters/redis:crc16_lib"],
)
