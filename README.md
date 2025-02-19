# Homebridge Triones LED Light Fluter Plug in

This plug-in enables you to control your Happy Lightning LED Fluter like in link below:

https://www.amazon.de/APP-Steuerung-Flutlichtstrahler-Au%C3%9Fenstrahler-Wasserdicht-Stimmungslichter/dp/B07RH6L2MC/ref=asc_df_B07RH6L2MC/?tag=googshopde-21&linkCode=df0&hvadid=354526888989&hvpos=&hvnetw=g&hvrand=12516609704161754213&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9043043&hvtargid=pla-792640354079&psc=1&th=1&psc=1&tag=&ref=&adgrpid=77086785812&hvpone=&hvptwo=&hvadid=354526888989&hvpos=&hvnetw=g&hvrand=12516609704161754213&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9043043&hvtargid=pla-792640354079

## New Version

```shell
npm install -g homebridge-magic-triones
```

## Connecting and setting up

The light bulb uses Bluetooth low energy. This means that your Raspberry Pi needs to have Bluetooth
in some way. You will need to know the mac address of the light bulb. You can discover it by
installing bluez and everything to your Raspberry Pi. A possible guide can be found
[here](http://www.elinux.org/RPi_Bluetooth_LE). However, you don't need to compile it yourself.
I find the version in the repositories to be sufficient. You can then discover the mac address
by running the command shown below. The mac is "FB:00:E0:82:AA:1F" in this case.

```shell
	$ sudo hcitool lescan
	LE Scan ...
	FF:FF:C8:5D:68:9E Eve
	FF:FF:C8:5D:68:9E Eve Thermo
	33:03:44:44:AA:5C (unknown)
	33:03:44:44:AA:5C Eve Door
	FB:00:E0:82:AA:1F (unknown)
	22:20:7B:99:D3:AF (unknown)
	FB:00:E0:82:AA:1F LEDBLE-A582661F    <--- this is your Fluter
	22:20:7B:99:D3:AF (unknown)
```

## Installation

Run the following command

```shell
npm install -g homebridge-magic-triones
```

Chances are you are going to need sudo with that.

## Config.json file

```json
{
    "accessory": "homebridge-magic-triones",
    "name": "Fluter A",
    "mac": "FB:00:E0:82:AA:1F",
}
```

| Key       | Description                                                                                                                                                                                                                                                       |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| accessory | Required. Has to be "homebridge-magic-triones"                                                                                                                                                                                                                             |
| name      | Required. The name of this accessory. This will appear in your Homekit app                                                                                                                                                                                        |
| mac       | Required. The mac address that you discovered earlier                                                                                                                                                                                                             |
| handle    | Optional. The handle that is used by the bulb for setting on/off and colors. This basically works like a key and you are writing the value. Use 46 for the newer(?) version of the bulbs. The standard value for the older(?) version is integrated into the code |

## Issues

This software comes with no warranty. It works for me and it might for you.

## Credit

I used the codes that were discovered by the author of this [post](https://bene.tweakblogs.net/blog/12447/connect-a-bluetooth-lightbulb-to-philips-hue). His findings were also used in his [repository](https://github.com/b0tting/magicbluehue). If the author reads this, I did not find your name on your blog. You can send me a message and I'll gladly add your name.

Another thanks to Garry Tan for the conversion methods. See his post [here](http://axonflux.com/handy-rgb-to-hsl-and-rgb-to-hsv-color-model-c).
