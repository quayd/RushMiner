# RushMiner pre-release v0.2.14

https://github.com/quayd/RushMiner/releases/latest

FPGA Miner w/Zetheron Bitstreams

## Description

FPGA Miner Featurees:
- multi-device per running instance.
- bitstream loading in-app
- auto-clocking based on: temperature (hardware error rate and amp/power to come with supported devices).
- voltage control in-app (currently relies on TeamRedMiner to set the voltage but aim to support native voltage control soon)
- scriptable
- TCP/IP support (requires tool to forward device USB packets to TCP; ex. sqrl_bridge, socat, netcat, etc.)

Future Features:
- Dynamic loading/resetting of devices.
- Remote access API's for query and control
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
## Example Usage
* Note: currently for voltage control you need to separately place the teamreadminer executable `teamredminer/teamredminer` in the rushminer sub-directory `util`.
```
sudo ./rushminer --log-level=info --no-ui --key-input --open-no-res -p rushtest -o stratum+tcp://ton.hashrate.to:4002 -t gram -u "UQAZwEyMpjkLNP3I0ytqWT2N1oanX06hwM10gyN4KljABvT5"  \
    --ftdi-cmd="monitor -t 5500 -p 350 --unit-count=1 -v user" \
    --ftdi-cmd="ramp -t 0 -i" \
    --ftdi-cmd="setvolt -D C1100,FK33 -T 650,650 -t 90 --progress 4" \
    --ftdi-cmd="verify --max-temp=35 --max-clock=35 --action=quit" \
    --ftdi-cmd="config --max-clock=660 --jtag=0" \
    --ftdi-cmd="-g -t C1100 load -f bitstreams/C1100/GRAM_C1100_Top.bit -f bitstreams/C1100/W1.bit -f bitstreams/C1100/W2.bit -f bitstreams/C1100/W3.bit -f bitstreams/C1100/W4.bit" \
    --ftdi-cmd="-g -t FK33 load -f bitstreams/FK33/GRAM_FK33_Top.bit -f bitstreams/FK33/F1.bit -f bitstreams/FK33/F2.bit" \
    --ftdi-cmd="-g -t CVP13 load -f bitstreams/CVP/GRAM40_CVP13_Top_B.bit -f bitstreams/CVP/K1.bit -f bitstreams/CVP/K2.bit -f bitstreams/CVP/K3.bit -f bitstreams/CVP/K4.bit -f bitstreams/CVP/K5.bit -f bitstreams/CVP/K6.bit -f bitstreams/CVP/K7.bit -f bitstreams/CVP/K8.bit" \
    --ftdi-cmd="monitor -t 5500 -p 200 --unit-count=1" \
    --ftdi-cmd="-g -t C1100 ramp -t 350"  \
    --ftdi-cmd="-g -t FK33 ramp -t 420" \
    --ftdi-cmd="-g -t CVP13 ramp -t 280" \
    --ftdi-cmd="-x ramp -t 10"
```
