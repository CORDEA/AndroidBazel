load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:jvm.bzl", "jvm_maven_import_external")

android_sdk_repository(
        name = "androidsdk",
        api_level = 29
)

RULES_JVM_EXTERNAL_TAG = "2.3"
RULES_JVM_EXTERNAL_SHA = "375b1592e3f4e0a46e6236e19fc30c8020c438803d4d49b13b40aaacd2703c30"

http_archive(
    name = "rules_jvm_external",
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    sha256 = RULES_JVM_EXTERNAL_SHA,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
        artifacts = [
                "com.android.tools.build:gradle:3.4.1",
                "org.jetbrains.kotlin:kotlin-gradle-plugin:1.3.40",
                "org.jetbrains.kotlin:kotlin-stdlib-jdk7:1.3.41",
                "androidx.appcompat:appcompat:1.0.2",
                "androidx.core:core-ktx:1.0.2",
                "androidx.constraintlayout:constraintlayout:1.1.3",
                "com.google.android.material:material:1.0.0",
                "junit:junit:4.12",
                "androidx.test:runner:1.2.0",
                "androidx.test.espresso:espresso-core:3.2.0"
        ],
        repositories = [
                "https://jcenter.bintray.com/",
                "https://maven.google.com",
        ]
)


rules_kotlin_version = "legacy-modded-0_26_1-02"
rules_kotlin_sha = "245d0bc1511048aaf82afd0fa8a83e8c3b5afdff0ae4fbcae25e03bb2c6f1a1a"
http_archive(
    name = "io_bazel_rules_kotlin",
    urls = ["https://github.com/cgruber/rules_kotlin/archive/%s.zip" % rules_kotlin_version],
    type = "zip",
    strip_prefix = "rules_kotlin-%s" % rules_kotlin_version,
    sha256 = rules_kotlin_sha,
)

# rules_kotlin_compiler_release = {
    # "urls": [
        # "https://github.com/JetBrains/kotlin/releases/download/v1.3.41/kotlin-compiler-1.3.41.zip",
    # ],
    # "sha256": "c44ab6866895606e408b60934ebe45d4befcbc33ea0e4ea73c4b3b89ad770132",
# }

# http_archive(
    # name = "io_bazel_rules_kotlin",
    # urls = ["https://github.com/bazelbuild/rules_kotlin/archive/%s.zip" % rules_kotlin_version],
    # type = "zip",
    # strip_prefix = "rules_kotlin-%s" % rules_kotlin_version
# )

load("@io_bazel_rules_kotlin//kotlin:kotlin.bzl", "kotlin_repositories", "kt_register_toolchains")
# kotlin_repositories(compiler_release=rules_kotlin_compiler_release)
kotlin_repositories()
kt_register_toolchains()
