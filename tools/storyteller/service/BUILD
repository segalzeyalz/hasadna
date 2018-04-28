package(default_visibility = ["//visibility:public"])
load("@org_pubref_rules_protobuf//java:rules.bzl", "java_proto_library")

java_proto_library(
    name = "service_lib",
    protos = ["service.proto"],
    verbose = 1,
    with_grpc = True,
)

java_library(
    name = "service",
    srcs = [
        "StorytellerService.java",
    ],
    deps = [
        ":service_lib",
        "@startup_os//common/firestore",
        "@startup_os//tools/local_server/service:auth_service",
        "//third_party/maven/io/opencensus:opencensus_contrib_grpc_metrics",
        "@org_pubref_rules_protobuf//java:netty_runtime_deps",
        "@startup_os//common/flags",
    ],
)

java_binary(
    name = "test_tool",
    srcs = [
        "TestTool.java",
    ],
    main_class = "tools.storyteller.service.TestTool",
    deps = [
        "//external:jar/com/google/protobuf/protobuf_java",
        "@startup_os//common",
        ":service",
        ":service_lib",
        "//third_party/maven/io/opencensus:opencensus_contrib_grpc_metrics",
        "@org_pubref_rules_protobuf//java:grpc_compiletime_deps",
        "//third_party/maven/org/slf4j:slf4j_simple",

    ],
)