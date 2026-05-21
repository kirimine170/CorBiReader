# Wireless transport

CorBi Reader uses Bluetooth Low Energy as the first wireless transport.

## Device role

The M5 StickC Plus advertises as `CorBi` and acts as a BLE peripheral. The PC-side Core acts as the BLE central and reads CorBi service characteristics.

## Service

- Pulse oximeter service: `c360fb9d-497f-4a0d-bfd3-6cbecd1786e1`

## Characteristics

- IR data / heart-rate placeholder: `0c1f518c-ffdf-4b0f-8f2f-ca1edc6dabae`
- Red data / SpO2 placeholder: `1d5b21fa-1a88-4ccb-8be8-9d8f07b0180c`

The raw-data branch extends this shape with an order characteristic so receivers can detect missing or repeated payloads.

## Scope

USB serial remains useful for flashing and debug logs. Health data transport should use BLE so the device can run untethered after upload.
