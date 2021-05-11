# George's Chisel + CIRCT workspace

This project is meant to be used via VSCode's Remote Containers Extention. You should be able to just open this folder in VSCode and select "Reopen in Container" in the popup that hopefully shows up. This option should also be available via the task selection UI (command-shift-P on macOS)

`llvm/circt` should be checked out under the `circt` folder (I don't use submodules to avoid pinning a particular commit). `sbt` is available inside the container and other interesting projects can be checked out alongside `circt` (some good examples are `sifive/chisel-circt-demo`  and `ucb-bar/chisel-tutorial`).

## Building CIRCT

`circt` can be built using the CMake Tools extension which should be automatically installed inside the remote container when VSCode brings it up. The first thing you should do is run the `CMake: Configure`  task using the task selection UI (command-shift-P on macOS). If you are asked to select a kit, select "Clang 10". This should add CMake affordances to the bottom bar, including a "Build" button which can be used to build `circt`. The container is set up so that `firtool` will end up in the container's `PATH`. You can interact with the container's environment via VSCode's integrated terminal feature.

## Compiling Chisel projects

The exact method for compiling Chisel code will be project-specific, but `sbt` is the root build tool and should be available in the container's `PATH`. For `ucb-bar/chisel-tutorial`, you can use a command like `sbt "test:runMain solutions.Launcher Counter --no-run-frrtl"` to generate FIRRTL artifacts, which you can then convert to MLIR using a command like `firtool Counter.fir --format=fir -mlir --annotation-file Counter.anno.json` (run in `test_run_dir/solutions/Counter`).
