## TWRP-Test AOSP Manifest

This branch is based on android16.0.0_r1.

### Getting Started

To get started with AOSP sources to build TWRP, you'll need to get familiar
with [Git and Repo](https://source.android.com/source/using-repo.html).

To initialize your local repository using the AOSP trees to build TWRP, use a command like this:

    repo init -u https://github.com/TWRP-Test/platform_manifest_twrp_aosp.git -b twrp-16.0

To initialize a shallow clone, which will save even more space, use a command like this:

    repo init --depth=1 -u https://github.com/TWRP-Test/platform_manifest_twrp_aosp.git -b twrp-16.0

Then to sync up:

    repo sync

Then to setup the build:

     cd <source-dir>; export ALLOW_MISSING_DEPENDENCIES=true; . build/envsetup.sh; lunch twrp_<device>-bp2a-eng

The build target is dependent on the device, and should reflect the location of stock recovery on the device. Issue the build command that applies to your device:

- Recovery partition: `mka recoveryimage`
- Boot image ramdisk: `mka bootimage`
- Vendor_boot image ramdisk: `mka vendorbootimage`

### Special Notes for this branch

- For android devices with Weaver+Strongbox+OMAPI.
- Device makefile in the device tree and dependencies file should use the "twrp" prefix.
- FDE decryption is not presently supported in this branch.
