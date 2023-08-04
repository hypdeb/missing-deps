# Bazel Issue Repro
This is a repository to reproduce an issue I'm facing with Bazel
* Have llvm with clang, libcxx and libc++abi installed under /usr/local/llvm or adjust the toolchain accordingly for your installation path.
* Run `bazel test --config=clang --test_output=all //tests:test_nothing`
* Bazel produces:
```
this rule is missing dependency declarations for the following files included by 'googletest/src/gtest-assertion-result.cc':
  '/home/jdebache/.cache/bazel/_bazel_root/bc03f42e2f15d0eae70f56c4a789b681/external/com_google_googletest/googletest/include/gtest/gtest-assertion-result.h'
  '/home/jdebache/.cache/bazel/_bazel_root/bc03f42e2f15d0eae70f56c4a789b681/external/com_google_googletest/googletest/include/gtest/gtest-message.h'
  '/home/jdebache/.cache/bazel/_bazel_root/bc03f42e2f15d0eae70f56c4a789b681/external/com_google_googletest/googletest/include/gtest/internal/gtest-port.h'
  '/home/jdebache/.cache/bazel/_bazel_root/bc03f42e2f15d0eae70f56c4a789b681/external/com_google_googletest/googletest/include/gtest/internal/custom/gtest-port.h'
  '/home/jdebache/.cache/bazel/_bazel_root/bc03f42e2f15d0eae70f56c4a789b681/external/com_google_googletest/googletest/include/gtest/internal/gtest-port-arch.h'
```
although those headers are definitely included by `gtest`.