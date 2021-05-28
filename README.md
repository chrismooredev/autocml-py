# AutoCML

# Authentication
This library (and associated scripts) supports authentication via environment variables. This library supports a variety of different variable names, meant to suit the different names Cisco already uses.

|Purpose|This Library|VIRL Library|Breakout Tool|Example|
|--|--|--|--|--|
|CML Controller|`CML_HOST`|`VIRL2_URL`|`BREAKOUT_CONTROLLER`| 192.168.0.50
|Username|`CML_USER`|`VIRL2_USER`|`BREAKOUT_USERNAME`|admin|
|Password (Base-64)|`CML_PASS64`|||`cGFzc3dvcmQ=`|
|Password|`CML_PASS`|`VIRL2_PASS`|`BREAKOUT_PASSWORD`|password|


Any combination of the above variables can be used, although the leftmost variable name will be prioritized in case of conflicts. Using `CML_PASS64` is recommended (and prioritized over other password variables) to prevent the likelyhood of successful shoulder-surfers.

# Scripts

This library includes common scripts/commands useful for administrative purposes, or for automating common lab scenarios.

## cml-verify-ints

Asserts a lab's interfaces against a .csv file. The csv file must have exactly three columns, (device ID/label, interface, and IP address (with optional CIDR notation)) and may look like the following:

```csv
Label,Int,IPv4
n0,GigabitEthernet0/0,192.168.0.24/26
R2,Fa0/2,10.1.34.2/24
R3,L1,10.255.0.3/32
```

One ran, it will print a report showing which interfaces match, or do not match. Interfaces not listed will not be checked.

Can also dump a CSV of interfaces, that can later be used with this utility to double-check interface addresses.

Also has a flag to emit results as JSON, although it cannot read in JSON inputs.

## cml-bulk-yaml

Allows for downloading/uploading lab YAMLs in bulk for archival purposes. Useful when migrating YAML labs files from one CML controller to another (like for a fresh upgrade).

## cml-dump-cfgs (WIP)

## cml-dump-cmds (WIP)

## cml-dump-pings (WIP)

## cml-pcap (WIP)

## cml-start-session (WIP)

Opens a tabbed terminal emulator to have a tab for each node's console within a lab.
