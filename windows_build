# Bitcoin Core – Windows Build & Run Documentation

**Author:** Abhijit Rathod  
**Environment:** Windows 10/11, MSVC, CMake, vcpkg, Qt6  
**Build Type:** Bitcoin Core (GUI + Node)

## 1. Bitcoin Core Library Dependencies

### 1.1 Core Libraries
- Boost (60+ modules)
- Libevent
- PCRE2
- Zlib
- SQLite3
- OpenSSL (libcrypto)

### 1.2 Bitcoin-Specific Libraries
- LevelDB
- CRC32C
- MiniSketch
- ZeroMQ

### 1.3 GUI (Qt6) Libraries
- Qt6Core
- Qt6Gui
- Qt6Widgets
- Qt6Network
- Qt6Svg
- Qt6Test  
**Platform plugin required:** `platforms/qwindows.dll`

### 1.4 Additional Libraries
- qrencode
- libpng
- iconv
- double-conversion

## 2. Build Steps (Windows)

### 2.1 Install vcpkg
```
git clone https://github.com/microsoft/vcpkg
cd vcpkg
.ootstrap-vcpkg.bat
.cpkg integrate install
```

### 2.2 Configure CMake
```
cmake -DVCPKG_TARGET_TRIPLET=x64-windows ^
      -DBUILD_GUI=ON ^
      -DCMAKE_TOOLCHAIN_FILE=C:/Users/Abhijit/vcpkg/scripts/buildsystems/vcpkg.cmake ^
      -S C:/Users/Abhijit/repos/bitcoin ^
      -B C:/Users/Abhijit/repos/bitcoin/out/build/vs2022 ^
      -G "Visual Studio 17 2022" -A x64
```

### 2.3 Build Bitcoin
```
cmake --build C:/Users/Abhijit/repos/bitcoin/out/build/vs2022 --config Release
```

## 3. Output Folder Structure

```
out/build/vs2022/
│
├── src/
│   ├── Release/
│   │   ├── bitcoind.exe
│   │   ├── bitcoin-cli.exe
│   │   ├── bitcoin-wallet.exe
│   │   └── bitcoin-tx.exe
│
└── src/qt/Release/
    ├── bitcoin-qt.exe
    ├── Qt6Core.dll
    ├── Qt6Gui.dll
    ├── Qt6Widgets.dll
    ├── platforms/qwindows.dll
    ├── imageformats/
    └── styles/
```

## 4. Fix Qt Platform Plugin Error

If you get:

**“No Qt platform plugin could be initialized”**

Copy:

`qwindows.dll`  
from:
```
C:/Users/Abhijit/vcpkg/installed/x64-windows/plugins/platforms/
```
into:
```
out/build/vs2022/src/qt/Release/platforms/
```

## 5. Running Bitcoin Core

### 5.1 GUI Wallet
```
bitcoin-qt.exe
```

### 5.2 Daemon
```
bitcoind.exe
bitcoind.exe -daemon
```

### 5.3 CLI
```
bitcoin-cli.exe getblockchaininfo
```

## 6. Pruned Mode (5–7GB Instead of 700GB)
Create:
```
%APPDATA%/Bitcoin/bitcoin.conf
```
Add:
```
prune=550
```

or:
```
bitcoin-qt.exe -prune=550
```

## 7. Testnet Mode
```
bitcoin-qt.exe -testnet
bitcoind.exe -testnet
bitcoin-cli.exe -testnet getblockchaininfo
```

## 8. Regtest Mode (Instant Mining)
```
bitcoind.exe -regtest -daemon
bitcoin-cli.exe -regtest generatetoaddress 1 <your_address>
```

---

Documentation Complete.
