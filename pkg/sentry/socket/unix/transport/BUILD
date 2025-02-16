load("//tools:defs.bzl", "go_library")
load("//tools/go_generics:defs.bzl", "go_template_instance")

package(licenses = ["notice"])

go_template_instance(
    name = "queue_mutex",
    out = "queue_mutex.go",
    package = "transport",
    prefix = "queue",
    substrs = {
        "genericMark": "unixQueue",
    },
    template = "//pkg/sync/locking:generic_mutex",
)

go_template_instance(
    name = "stream_queue_receiver_mutex",
    out = "stream_queue_receiver_mutex.go",
    package = "transport",
    prefix = "streamQueueReceiver",
    substrs = {
        "genericMark": "streamQueueReceiver",
    },
    template = "//pkg/sync/locking:generic_mutex",
)

go_template_instance(
    name = "endpoint_mutex",
    out = "endpoint_mutex.go",
    package = "transport",
    prefix = "endpoint",
    substrs = {
        "genericMark": "unixEndpoint",
    },
    template = "//pkg/sync/locking:generic_mutex",
)

go_template_instance(
    name = "transport_message_list",
    out = "transport_message_list.go",
    package = "transport",
    prefix = "message",
    template = "//pkg/ilist:generic_list",
    types = {
        "Element": "*message",
        "Linker": "*message",
    },
)

go_template_instance(
    name = "queue_refs",
    out = "queue_refs.go",
    package = "transport",
    prefix = "queue",
    template = "//pkg/refsvfs2:refs_template",
    types = {
        "T": "queue",
    },
)

go_template_instance(
    name = "host_connected_endpoint_refs",
    out = "host_connected_endpoint_refs.go",
    package = "transport",
    prefix = "HostConnectedEndpoint",
    template = "//pkg/refsvfs2:refs_template",
    types = {
        "T": "HostConnectedEndpoint",
    },
)

go_library(
    name = "transport",
    srcs = [
        "connectioned.go",
        "connectioned_state.go",
        "connectionless.go",
        "connectionless_state.go",
        "endpoint_mutex.go",
        "host.go",
        "host_connected_endpoint_refs.go",
        "host_iovec.go",
        "host_unsafe.go",
        "queue.go",
        "queue_mutex.go",
        "queue_refs.go",
        "save_restore.go",
        "stream_queue_receiver_mutex.go",
        "transport_message_list.go",
        "unix.go",
    ],
    visibility = ["//:sandbox"],
    deps = [
        "//pkg/abi/linux",
        "//pkg/atomicbitops",
        "//pkg/bufferv2",
        "//pkg/context",
        "//pkg/errors/linuxerr",
        "//pkg/fdnotifier",
        "//pkg/ilist",
        "//pkg/log",
        "//pkg/refs",
        "//pkg/refsvfs2",
        "//pkg/sentry/hostfd",
        "//pkg/sentry/inet",
        "//pkg/sentry/uniqueid",
        "//pkg/sync",
        "//pkg/sync/locking",
        "//pkg/syserr",
        "//pkg/tcpip",
        "//pkg/unet",
        "//pkg/waiter",
        "@org_golang_x_sys//unix:go_default_library",
    ],
)
