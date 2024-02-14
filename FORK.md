# ﻿Messtastik (in Development)
## My Meshtastic Config and Development Fork
Use MQTT phone proxy setting, to keep bluetooth BLE default (random PIN, for easier WiFi code elimination and better security). Ignore WiFi IP based security option.
Use EU_898 as the region.
Keep default LONG_FAST free of MQTT. (channel 0).
* 0 - Default `LongFast` (chat and default happy telemetry).
Make VERY_LONG_SLOW use MQTT if possible ... later, channels 1 to 4. (make it on channels 1 to 4 too for fun, if possible).
An algorithm using decode frequency (of packets) would be good here, as the extra (9?) dB and "phone proxy" (no WiFi expected) net gateway would provide "fill".
Then channels 1 to 4 are considered "dark mode entertainment". 
* 1 - `admin` (remote admin).
* 2 - `gpio` (for projects).
* 3 - `serial` (for projects).
* 4 - `mqtt` (`msh/2/json/mqtt/` automation channel, open (or close) MQTT downlink).
Maybe unlikely though as the LoRa data format might be fixed across channels based on PRIMARY, but could be. This would make channels 1 to 4, leaving 5 to 7 for other purposes.
* 5 - `mil` (pentagroawrne tactical nuts).
* 6 - `logic` (it's supposed to make sense).
* 7 - `dreams` (is it supposed to make sense?).
## QR Code (joining the may helm)
This excludes the `admin` channel and so on systems without `admin` might exclude `dreams`. Sharing `admin` keys is bad, so set up and get channel 7 too.
It also excludes the `gpio` and `mqtt` downlink channels perhaps excluding `mil` too. It's ok to allow the `serial` channel as it can be security mitigated.

## Experimental Code Reductions and Additions
* Remove WiFi usage.
* Enforce Serial as API Protobuf port.
* Other packet formats.
* Status ping.
* Spam elimination.
## Server and Application Additions
* Various protocol bridges.
* Various service tool bots.
## Branch Principles and Naming Conventions
To maintain PR compatibility with feature expansion while also having code reduction all features are developed on a branch and the PR is from the branch before the merge into the reduce branch. The reduce branch is a pure code reduction branch, not designed to PR to upstream. The systematic process then becomes merge upstream into mai/master, create a merge/reduce branch, apply edits to allow a merge of the reduce branch, apply feature branches to the release branch, branched of the reduce branch. Naming branches in the form kind-iso-date allows tracking use, while tags can be used for more effective purpose tags in any automating scripts.
* upstream AKA master -> (reduce MERGE | feature BRANCH)
* feature -> (upstream PR | release MERGE)
* reduce -> release MERGE
* release MAKE
## The Fork’s Purpose
The fork is not intended as a code split “political” argument, but as a general code resource designed principally with the idea of it being an ESP32 general coding repository, while maintaining “why shouldn’t it be a meshtastic client as well?” even though it might not maintain all features (such as WiFi app connectivity to phones). It is not even the fork’s purpose to maintain stability if “reduced” upstream features get used and no unstripped code exists to facilitate the misunderstanding.
# Useful Info
* `SPIFFS` is in `data` folder and must make and upload filesystem separate from code. Alien then `PROJECT TASKS/heltec-v3/Platform/...`. (8 MB limit).
