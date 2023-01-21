# [T4CORUN ZMK Config](https://github.com/T4CORUN/zmk-config)

## [Rollow](https://www.barbellboards.com/product/rollow)

Rollow is one of the first split keyboards with dedicated thumb encoders... It's inspired by the ergonomics of a Ferris and the elegance of a Corne. While also influenced by my passion for the automotive customization scene.

This passion is represented in the small details like…

- A base plate designed with hot-swap socket cutouts, allowing sockets to fit within the plate making Rollow one of the lowest sitting hot-swappable split keyboards (Excluding Mini Version).
- Custom Inset OLED covers add additional protection to your OLEDs, while maintaining a balanced, sleek, and flush appearance to your board.
- Gasket-like sound dampening layer to minimize unwanted rattles and noise.

My Notes:

- This is my first time using ZMK
- ZMK does not officially define the Rollow Shield and does not support Peripheral Side Encoder as of 2022-Oct-25
- Keymap is heavily inspired by Manna Harbor Miryoku. I flipped some things around and made some operations doable with the left side so I can keep using the mouse
- Uses [infused-kim](https://github.com/infused-kim) repo to enable peripheral side encoder
- Used [tutuuXY](https://github.com/TutuuXY/zmk-config)'s repo to get shield definition
- My [Issues](https://github.com/T4CORUN/zmk-config/issues)
- Things I use that are missing in ZMK

	```text
	Mouse Emulation
	Dynamic Macros
	```

## Build

Inside the zmk root directory you simply run the following commands depending on the desired
keyboard config:

### Reviung41

```bash
west build -b nice_nano_v2 -d build/reviung41 -- -DSHIELD=reviung41 -DZMK_CONFIG="${HOME}/git/personal/zmk-config/config"
```

### Rollow

```bash
for side in left right; do
  west build -b nice_nano_v2 -d "build/rollow_${side}" -- -DSHIELD=rollow -DZMK_CONFIG="${HOME}/git/personal/zmk-config/config"
done
```

## Flashing

Put the nice nano into flash mode. To do that push the reset button two times and the control LED will begin to pulse slowly
You may then 'mount' the board and copy a firmware onto it, e.g. for the Reviung41:

```bash
udisksctl mount -b /dev/disk/by-label/NICENANO && cp /path/to/zmk/build/reviung41/zephyr/zmk.uf2 "/run/media/$(whoami)/NICENANO"
```

That's it, your new firmware is active 😁
