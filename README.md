# Nitara CLV4 — firmware releases

Firmware binaries for the **CLV4 WiFi connector** (ESP32-S3), published here so devices can
download updates over HTTPS.

This repository is **public on purpose**: a connector pulls its update with no login, exactly as it
would from a production update server. It contains **binaries only** — no source code.

## No credentials in these files

Builds published here are produced **without** the broker credentials file, so they fall back to a
public test broker. Never publish a build made with real credentials: the URI, username and
password are compiled into the binary as plaintext and would be readable by anyone.

## Updating a device

```json
{"command":"fota_start","url":"https://github.com/Niranjan107/NC_firmware_releases/releases/download/<tag>/NCLite_ESP32S3.bin"}
```

Progress and the result are reported on `clv4/<device-id>/resp`. The device writes the image to its
spare OTA slot, reboots, and confirms it only after running 60 seconds without crashing — a
crash-looping update reverts on its own.

Source, documentation and the command reference live in the private `NC_esp32s3_wifi` repository.
