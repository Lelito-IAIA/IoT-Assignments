### Virtual Environment Station 1
## About
This folder contains the code of the virtual environment station 1

## Setting up Virtual Envirotnment Station
When running the virtual environment station, we must configure some global addresses,
as the RSMB doesn't seems to be able to handle link-local addresses. So for a
single RIOT native instance, we can do the following:

1. Setup `tap` and `tapbr` devices using RIOT's `tapsetup` script:
```
./RIOTDIR/dist/tools/tapsetup/tapsetup
```

2. Assign a site-global prefix to the `tapbr0` interface (the name could be
   different on OSX etc):
```
sudo ip a a fec0:affe::1/64 dev tapbr0
```

3. Assign a site-global address with the same prefix to the RIOT `native`
   instance:
```
ifconfig 5 add fec0:affe::99
```


## Usage
This example maps all available MQTT-SN functions to shell commands. Simply type
`help` to see the available commands. The most important steps are explained
below:

- To connect to a broker, use the `con` command:
```
con fec0:affe::1 1885
```
- To start publishing the randomly generated values, just execute the following command
```
pub_values
```
