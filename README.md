# Bash: Azure Storage DataLake C++ Standalone Sample Consuming Azure SDK via VcPkg

This is supposed to be used only for Azure C++ team for one-off verification of VcPkg integration.

It pulls and builds the Azure SDK, from my fork (https://github.com/antkmsft/azure-sdk-for-cpp/).
The releases I have there are based on Monday Jan 1st, 2021 master branch of our repo.

## Instructions

* Clone this sample repo.
* Rename your current vcpkg directory.
* Clone antkmsft's fork of the vcpkg repo: `git clone https://github.com/antkmsft/vcpkg.git`, so that it exists where your old vcpkg directory used to be.
* Switch to azure-sdk-for-cpp branch: `git checkout azure-sdk-for-cpp`
* Install DataLake SDK: `vcpkg install azure-storage-files-datalake-cpp:x64-windows-static`.
* Build this sample. All should succeed.

## Further Experimentation

* Try other triplets.
* Try other platforms: mac, linux.
* Try also installing azure-identity-cpp, azure-storage-files-shares-cpp (azure-storage-files-datalake-cpp should already bring up core, storage common, and storage blobs).
* Let's go through a versioned dependency (modify `find_package` to specify version).
* Let's go through an upgrade scenario.
* Try another sample using another library. This code, for example, is an adaptation of the DataLake sample we have in our SDK.

# Other
* Let's submit a PR to VcPkg and verify that the build succeeds in their pipelines - https://github.com/microsoft/vcpkg/pull/15471

## Undoing vcpkg
* delete the vcpkg folder you cloned from my fork, rename your old vcpkg directory back to its original name.
