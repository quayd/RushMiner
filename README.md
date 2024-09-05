# RushMiner pre-release v0.2.9

https://github.com/quayd/RushMiner/releases/latest


FPGA Miner w/Zetheron Bitstreams

## Description

FPGA Miner Featurees:
- multi-device per running instance.
- bitstream loading in-app
- voltage control in-app (currently relies on TeamRedMiner to set the voltage but aim to support native voltage control soon)
- scriptable
- TCP/IP support (requires tool to forward device USB packets to TCP; ex. sqrl_bridge, socat, netcat, etc.)

Future Features:
- Remote access API's
- Native voltage control
- Solo-mode

RushMiner supports all the abilities of RushDev, so refer to RushDev github for documentation: https://github.com/quayd/RushDev

## OS Compatibility

| Operating System  | Functionality |
|-------------------|:-------------:|
| Ubuntu 16.04      | N             |
| Ubuntu 18.04      | N             |
| Ubuntu 20.04      | Y             |
| Ubuntu 22.04      | Y             |
| Windows 10        | N             |
| Windows 11        | N             |

* Ubuntu subversions in between main .04 releases are untested
* HiveOS and MMPOS run off of Ubuntu 18.04, 20.04 or 22.04 depending on version. In theory they should work but are not yet confirmed.
* Windows version coming shortly.
