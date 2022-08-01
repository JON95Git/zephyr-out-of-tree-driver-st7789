# Zephyr out-of-tree driver ST7789-no-cs
A simple example to demonstrate how to create an out-of-tree driver in Zephyr RTOS.
The custom driver is an altered version of ST7789v device driver for a display
without CS pin.

The application example creates a [LVGL](https://lvgl.io/) widget in 
Zephyr RTOS running on a [nRF52840_mdk](https://wiki.makerdiary.com/nrf52840-mdk/).

## Dependencies

- Zephyr RTOS v3.1.0

## Helpul links

- https://blog.golioth.io/adding-an-out-of-tree-sensor-driver-to-zephyr/

- https://docs.zephyrproject.org/latest/samples/application_development/out_of_tree_driver/README.html

- https://github.com/zephyrproject-rtos/example-application


## Tree folder structure

```
.
├── CMakeLists.txt
├── drivers
│   └── zephyr
│       ├── CMakeLists.txt
│       ├── display
│       │   ├── CMakeLists.txt
│       │   ├── Kconfig
│       │   └── st7789v_no_cs
│       │       ├── CMakeLists.txt
│       │       ├── display_st7789v_no_cs.c
│       │       ├── display_st7789v_no_cs.h
│       │       └── Kconfig
│       ├── Kconfig
│       └── module.yml
├── dts
│   └── bindings
│       └── display
│           └── sitronix,st7789v-no-cs.yaml
├── Kconfig
├── nrf52840_mdk.overlay
├── prj.conf
└── src
    ├── lvgl_sample.c
    ├── lvgl_sample.h
    └── main.c
```

## Tests
It was tested in a `nRF52840_mdk` board.

## Pinout

| nRF52840_mdk |   ST7789   |
|--------------|------------|
|     P0.28    |    RES     |
|     P0.29    |  DC (CMD)  |
|     P0.27    |  SCK (SCL) |
|     P0.26    | MOSI (SDA) |

## How to build
```
$ west build -p auto -b nrf52840_mdk
```

## How to flash
```
$ west flash
```
## Application running

![capture](doc/nrf52840-st7789-lvgl.gif)
