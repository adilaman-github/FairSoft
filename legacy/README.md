# FairSoft (Legacy)

Table of Contents
* [Preface](#preface)
* [Installation from source](#installation-from-source)
* [Advanced topics and troubleshooting](#advanced-topics)
* [Tested systems](#tested-systems)
* [Included packages](#included-packages)

## Preface

Our classic bash/cmake based setup system
has been named "Legacy". It has been moved to the
sub-directory `legacy/` to distinguish it clearly
from the future Spack-based setup system
(for more information see [here](../docs/README.md)).
The latter will eventually replace the "Legacy" setup system
in a future release.

## Installation from source

Installing FairSoft is based on the standard CMake workflow.

### 1. Install system dependencies

Find the list of required system packages together with instructions
on how to install them in the [dependencies section](dependencies.md).

### 2. Clone the git repo

```
git clone -b <release> https://github.com/FairRootGroup/FairSoft
```

For `<release>` choose
* `apr22`, or `apr22p1`, ... - a particular release
* `apr22_patches` - always points to the latest patch release for the `apr22` release
* `master` - track the latest stable release (e.g. if `apr22` is the latest release `master` is the same as `apr22_patches`)
* `dev` - the bleeding edge development version

Discover releases here: https://github.com/FairRootGroup/FairSoft/releases

### 3. CMake configure step

```
cmake -S <path-to-source> -B <path-to-build> -C <path-to-source>/FairSoftConfig.cmake
```

* `<path-to-source>` shall point to the cloned git repo from the previous step
* `<path-to-build>` is a temporary directory of your choice where all of the package download, extraction, and building happens

Set the installation prefix and more customization options in the [`FairSoftConfig.cmake`](../FairSoftConfig.cmake) file itself.

**macOS users**: Notice [macOS SDK](advanced.md#macos-sdk)!

### 4. CMake build/install step

After a successful CMake configure step, you start the build/install step as follows:

```
cmake --build <path-to-build> [-j<ncpus>]
```

* `<path-to-build>` is the same directory as chosen in the previous configure step
* `-j<ncpus>` parallelize the build

### 5. Usage

```
export SIMPATH=<path-to-install>
```

Simply export an environment variable `SIMPATH` which points to the chosen install directory from step 2
and continue with the [FairRoot installation](https://github.com/FairRootGroup/FairRoot).

## Advanced topics

Find several advanced and troubleshooting topics in the [advanced section](advanced.md).

## Tested systems

The following systems are tested regularly. If you feel your system is missing,
please contact us.

| **OS Name** | **Arch** | **OS Version** | **Compiler** | **CMake** |
| --- | --- | --- | --- | --- |
| Archlinux  | x86_64 | latest| GCC 11.2.0                 | 3.23.1 |
| CentOS     | x86_64 | 7     | GCC 11.2.1 (devtoolset-11) | 3.17.5 (epel: cmake3) |
| Rockylinux | x86_64 | 8     | GCC 8.5.0                  | 3.20.2 |
| Debian     | x86_64 | 10    | GCC 8.3.0                  | 3.22.3 (`bootstrap-cmake.sh`) |
| Debian     | x86_64 | 11    | GCC 10.2.1                 | 3.18.4 |
| Fedora     | x86_64 | 33    | GCC 10.3.1                 | 3.19.7 |
| Fedora     | x86_64 | 34    | GCC 11.2.1                 | 3.20.5 |
| Fedora     | x86_64 | 35    | GCC 11.2.1                 | 3.22.2 |
| Fedora     | x86_64 | 36    | GCC 12.0.1 (20220413)      | 3.22.2 |
| macOS      | x86_64 | 12    | AppleClang 13, gfortran 11 | 3.23.0 (brew) |
| macOS      | x86_64 | 11    | AppleClang 13, gfortran 11 | 3.23.0 (brew) |
| macOS      | arm64  | 12    | AppleClang 13, gfortran 11 | 3.23.0 (brew) |
| OpenSUSE   | x86_64 | 15.2  | GCC 7.5.0                  | 3.17.0 |
| Ubuntu     | x86_64 | 20.04 | GCC 9.4.0                  | 3.16.3 |
| Ubuntu     | x86_64 | 22.04 | GCC 11.2.0                 | 3.22.1 |

## Included packages

| **Package** | **Version** | **URL** |
| --- | --- | --- |
| asio             | 1.19.1       | https://think-async.com/Asio/ |
| boost            | 1.78.0       | https://www.boost.org/ |
| clhep            | 2.4.5.1      | http://proj-clhep.web.cern.ch |
| dds              | 3.6          | http://dds.gsi.de |
| faircmakemodules | 1.0.0        | https://github.com/FairRootGroup/FairCMakeModules |
| fairlogger       | 1.11.0       | https://github.com/FairRootGroup/FairLogger |
| fairmq           | 1.4.50       | https://github.com/FairRootGroup/FairMQ |
| flatbuffers      | 1.12.0       | https://github.com/google/flatbuffers |
| fmt              | 8.1.1        | https://github.com/fmtlib/fmt |
| geant3           | 4-0_fairsoft | https://github.com/FairRootGroup/geant3 |
| geant4           | 11.0.1       | https://geant4.web.cern.ch |
| geant4_vmc       | 6-1          | https://github.com/vmc-project/geant4_vmc |
| hepmc            | 2.06.11      | http://hepmc.web.cern.ch |
| pythia6          | 428-alice1   | https://github.com/alisw/pythia6 |
| pythia8          | 8306         | https://pythia.org/ |
| root             | 6.26.02      | https://root.cern |
| vc               | 1.4.2        | https://github.com/VcDevel/Vc |
| vgm              | 5-0          | https://github.com/vmc-project/vgm |
| vmc              | 2-0          | https://github.com/vmc-project/vmc |
| zeromq           | 4.3.4        | https://github.com/zeromq/libzmq |
