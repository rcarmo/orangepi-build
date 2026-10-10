## Supported boards

Soc | Boards |
|:--|:--|
| Allwinner H6 | Orange Pi 3/3 LTS |
| Allwinner H616 | Orange Pi Zero2/Zero2w/Zero3 | 
| Allwinner T527 | Orange Pi 4A |
| Allwinner A733 | Orange Pi 4Pro | 
| Rockchip RK3399 | Orange Pi 4/4B/4 LTS/800 |
| Rockchip RK3566 | Orange Pi 3B/CM4 |
| Rockchip RK3588S | Orange Pi 5/5B/5Pro/CM5/CM5-tablet |
| Rockchip RK3588 | Orange Pi 5Plus/5MAX/5Ultra |
| Cix P1 | Orange Pi 6Plus |
| Starfive  JH7110 | Orange Pi RV |
| Ky X1 | Orange Pi RV2/R2S |

## Download links

- 中文链接：     http://www.orangepi.cn
- English link：http://www.orangepi.org

## Supported Host Systems
- Ubuntu 22.04

## EROFS kernel support

The shipped EROFS-capable kernel configurations enable built-in
`CONFIG_EROFS_FS=y`, LZ4 compressed images (`CONFIG_EROFS_FS_ZIP=y`), extended
attributes, POSIX ACLs and security labels. Older vendor kernels without an
EROFS configuration entry are unchanged; no driver backport is included.
Custom or previously saved kernel configurations still override these defaults.
Rebuild the kernel to apply the changes; existing prebuilt kernels are unaffected.

This does **not** change the system/root filesystem or image layout. To create
and mount a separate EROFS image, install `erofs-utils` on the machine where you
create it, then use, for example:

```sh
mkfs.erofs -zlz4hc data.erofs /path/to/data
sudo mount -t erofs -o loop,ro data.erofs /mnt
```

Check the shipped configuration defaults with `python3 tests/check-erofs-configs.py`.
