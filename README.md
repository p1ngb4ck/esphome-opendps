# esphome-opendps

`opendps`: control and monitor [OpenDPS](https://github.com/kanflo/opendps) bench power supplies (DPS5005 and
similar with the OpenDPS firmware) from ESPHome over their serial port - voltages, current, power and temperatures at
up to loop speed, output on / off, voltage and current limits, functions, brightness and lock, calibration, firmware
upgrades over the serial link, a TCP bridge for the OpenDPS desktop tools and a datalogger to a storage.

## Getting started

```yaml
external_components:
  - source: github://p1ngb4ck/esphome-opendps@main
    components: [opendps]

uart:
  id: opendps_uart
  tx_pin: GPIO17
  rx_pin: GPIO16
  baud_rate: 115200

opendps:
  id: dps
  uart_id: opendps_uart

sensor:
  - platform: opendps
    opendps_id: dps
    voltage_out:
      name: Output voltage
    current_out:
      name: Output current
```

Wire the ESP's TX to the supply's RX, RX to TX and GND to GND, at the supply's logic level.

## More

- **[esphome/components/opendps/README.md](esphome/components/opendps/README.md)**: every option, sensor, action,
  the datalogger, firmware upgrades, the TCP bridge.
- Examples: [example_basic.yaml](esphome/components/opendps/example_basic.yaml),
  [example_full.yaml](esphome/components/opendps/example_full.yaml),
  [example_ethernet.yaml](esphome/components/opendps/example_ethernet.yaml),
  [example_calibration.yaml](esphome/components/opendps/example_calibration.yaml).
- A Home Assistant dashboard card: [ha-card/](esphome/components/opendps/ha-card/).

## Branches

`pr/opendps` (the component); `main` contains it. Base: ESPHome `dev` at `1f70f86b47`. The datalogger writes through
the storage interface ([esphome-storage-interface](https://github.com/p1ngb4ck/esphome-storage-interface)).

## License

- ESPHome's own files, also where this repository changes them: the [ESPHome License](LICENSE) (MIT for the Python
  code and everything else, GPLv3 for the C++ runtime files).
- New files written for this repository (new components, their code, tests and documentation): MIT,
  [LICENSE-MIT](LICENSE-MIT).

## Thanks

Thank you, Johan Kanflo, for [OpenDPS](https://github.com/kanflo/opendps) - an open firmware that turned cheap
power supply modules into lab instruments.

## Branch structure

Each `pr/` branch holds one part of this topic on top of upstream and says in its `BRANCH.md` what it is based on. `main` holds all of them.

| Branch | Based on |
|---|---|
| `pr/opendps` | upstream only |
