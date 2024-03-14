# Manifest for building crDroid v7 for gtaxlwifi and gtanotexlwifi

`gtaxlwifi` is the codename for the WiFi-only variant of the Samsung Galaxy Tab A 10.1" (2016), with model SM-T580.

`gtanotexlwifi` is the codename for the WiFi-only variant of the Samsung Galaxy Tab A 10.1" (2016) **with S-Pen**, with model SM-P580.

Some extremely basic instructions:
- Make a new directory for crDroid sources and enter it:
```
mkdir cr-a11
cd cr-a11
```

- Initialize repo in this directory with the crDroid v7 android repository:
```
repo init -u https://github.com/crdroidandroid/android.git -b 11.0 --git-lfs --depth=1
```

- Clone this repository to .repo/local_manifests for roomservice.xml containing the repositories needed to build for these devices:
```
git clone https://github.com/EAZYBLACK/gtaxl-manifests.git -b crdroida11 .repo/local_manifests
```

- Sync all of the repositories in manifests (including crDroid manifests):
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags --optimized-fetch
```

- Finally, build as you like. For example, A build for gtaxlwifi:
```
. build/envsetup.sh
lunch lineage_gtaxlwifi-userdebug
make bacon -j$(nproc --all)
```
...or for gtanotexlwifi:
```
. build/envsetup.sh
lunch lineage_gtanotexlwifi-userdebug
make bacon -j$(nproc --all)
```
