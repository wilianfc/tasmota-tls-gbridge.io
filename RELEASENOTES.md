<img src="https://github.com/arendst/Tasmota/blob/master/tools/logo/TASMOTA_FullLogo_Vector.svg" alt="Logo" align="right" height="76"/>

# RELEASE NOTES

## Migration Information

See [migration path](https://tasmota.github.io/docs/#/Upgrading?id=migration-path) for instructions how to migrate to a major version. Pay attention to the following version breaks due to dynamic settings updates:

1. Migrate to **Sonoff-Tasmota 3.9.x**
2. Migrate to **Sonoff-Tasmota 4.x**
3. Migrate to **Sonoff-Tasmota 5.14**
4. Migrate to **Sonoff-Tasmota 6.x**
5. Migrate to **Tasmota 7.x**

--- Major change in parameter storage layout ---

6. Migrate to **Tasmota 8.1**
7. Migrate to **Tasmota 8.x**

While fallback or downgrading is common practice it was never supported due to Settings additions or changes in newer releases. Starting with release **v8.1.0 Doris** the Settings are re-allocated in such a way that fallback is only allowed and possible to release **v7.2.0 Constance**. Once at v7.2.0 you're on your own when downgrading even further.

## Supported Core versions

This release will be supported from ESP8266/Arduino library Core version **2.6.1** due to reported security and stability issues on previous Core version.

Although it might still compile on previous Core versions all support will be removed in the near future.

## Support of TLS

To save resources when TLS is enabled mDNS needs to be disabled. In addition to TLS using fingerprints now also user supplied CA certs and AWS IoT is supported. Read [full documentation](https://tasmota.github.io/docs/#/integrations/AWS-IoT)

## Initial configuration tools

For initial configuration this release supports Webserver based **WifiManager** or **Serial** based command interface only. Support for **WPS** and **SmartConfig** has been removed.

## Provided Binary Downloads

The following binary downloads have been compiled with ESP8266/Arduino library core version **2.6.1**.

- **tasmota.bin** = The Tasmota version with sensors. **RECOMMENDED RELEASE BINARY**
- **tasmota-BG.bin** to **tasmota-TW.bin** = The Tasmota version in different languages.
- **tasmota-lite.bin** = The Lite version without most sensors.
- **tasmota-knx.bin** = The Knx version without some features but adds KNX support.
- **tasmota-sensors.bin** = The Sensors version adds more useful sensors.
- **tasmota-ir** = The InfraRed Receiver and transmitter version allowing all available protocols provided by library IRremoteESP8266 but without most other features.
- **tasmota-display.bin** = The Display version without Energy Monitoring but adds display support.
- **tasmota-minimal.bin** = The Minimal version allows intermediate OTA uploads to support larger versions and does NOT change any persistent parameter. This version **should NOT be used for initial installation**.

[List](MODULES.md) of embedded modules.

[Complete list](BUILDS.md) of available feature and sensors.

## Changelog

### Version 8.1.0.3

- Change Lights: simplified gamma correction and 10 bits internal computation
- Fix Sonoff Bridge, Sc, L1, iFan03 and CSE7766 serial interface to forced speed, config and disable logging
- Fix commands ``Display`` and ``Counter`` from overruling command processing (#7322)
- Fix ``White`` added to light status (#7142)
- Fix Improved fade linearity with gamma correction
- Fix LCD line and column positioning (#7387)
- Fix Display handling of hexadecimal escape characters (#7387)
- Add command ``SetOption79 0/1`` to enable reset of counters at teleperiod time by Andre Thomas (#7355)
- Add command ``SetOption82 0/1`` to limit the CT range for Alexa to 200..380
- Add command ``ShutterButton <parameters>`` to control shutter(s) by to-scho (#7403)
- Add SerialConfig to ``Status 1``
- Add WifiPower to ``Status 5``
- Add support for DS1624, DS1621 Temperature sensor by Leonid Myravjev
- Add Zigbee attribute decoder for Xiaomi Aqara Cube
- Add support for ``AdcParam`` parameters to control ADC0 Current Transformer Apparent Power formula by Jodi Dillon (#7100)
- Add optional support for Prometheus using file xsns_91_prometheus.ino (#7216)
- Add experimental support for NRF24L01 as BLE-bridge for Mijia Bluetooth sensors by Christian Baars (#7394)
- Add support to BMP driver to enter reset state (sleep enable) when deep sleep is used in Tasmota
- Add support for gzipped binaries
