# Manifest for building CrDroid 13 for gtaxlwifi, gtaxllte, gtanotexlwifi, and gtanotexllte

`gtaxlwifi` is the codename for the WiFi-only variant of the Samsung Galaxy Tab A 10.1" (2016), with model SM-T580.

`gtaxllte` is the codename for the LTE variant of the Samsung Galaxy Tab A 10.1" (2016), with model SM-T585, and also with SM-T585N0 and SM-T585C for Korea and China respectively.

`gtanotexlwifi` is the codename for the WiFi-only variant of the Samsung Galaxy Tab A 10.1" (2016) **with S-Pen**, with model SM-P580, and also with SM-P583 for China.

`gtanotexllte` is the codename for the LTE variant of the Samsung Galaxy Tab A 10.1" (2016) **with S-Pen**, with models SM-P585, SM-P585M, SM-P585Y, SM-P585N0, and SM-P588C.

Some extremely basic instructions:

These assume you have a good Linux build environment prepared with all prerequisite dependencies installed. If not, you should be able to find out how to prepare a build environment, and what dependencies you should have installed for your specific Linux distribution, by searching elsewhere.

- Make a new directory for CrDroid 13 sources and enter it:
```
mkdir cr-13
cd cr-13
```

- Initialize repo in this directory with CrDroid's android.git repository:
```
repo init -u https://github.com/crdroidandroid/android.git -b 13.0 --git-lfs --depth=1

```

- Clone this repository to .repo/local_manifests for the manifest, gtaxl.xml, containing the repositories needed to build for these devices:
```
git clone https://github.com/EAZYBLACK/gtaxl-manifests.git -b crdroid13 .repo/local_manifests
```

- Sync all of the repositories in manifests (including LineageOS manifests):
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags --optimized-fetch
```

- Finally, build as you like. For example, for a recovery-installable package for gtaxlwifi:
```
. build/envsetup.sh
lunch lineage_gtaxlwifi-userdebug
mka bacon
```
