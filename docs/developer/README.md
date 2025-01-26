# Developer Information

## Building FAT CONTROLLER on drone

```
clone git@github.com:Ryder-Robots/fatcnt.git
mkdir build
cd build
cmake -S .. -B . 
cmake --build . --target install/strip
cmake --build . --target test
cmake -DCMAKE_INSTALL_PREFIX=/opt/fatcnt ..
cpack -G DEB 
```

## Installing

```
dpkg -i ./build/*.deb
systemctl start fatcnt
journalctl -uf fatcnt.service
```

## Table Of Contents

- [PS4 Controller](docs/developer/ps4_conroller.md)
- [MSP104 Command](docs/developer/commands/msp104.md)

