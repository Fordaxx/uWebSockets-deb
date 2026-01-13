# libuwebsockets-dev — Debian Package

Debian packaging for µWebSockets — a simple, secure & standards compliant web server for the most demanding of applications.

## About µWebSockets

- **Header-only C++17** library for high-performance web servers and WebSocket applications
- **Built on µSockets** for eventing, networking and cryptography
- **TLS 1.3** with optimized security and ~95% fuzzing coverage (OSS-Fuzz)
- **Battle proven**: powers major crypto exchanges handling billions in daily trade volume
- **Features**: URL router with wildcards, pub/sub for WebSockets, permessage-deflate compression
- **Apache License 2.0**

**Upstream**: [https://github.com/uNetworking/uWebSockets](https://github.com/uNetworking/uWebSockets)

## Quick Start

### Installing

```bash
sudo dpkg -i libuwebsockets-dev_*.deb
sudo apt-get install -f
```

### Building from source

```bash
sudo apt-get install debhelper-compat build-essential dpkg-dev
dpkg-source -x libuwebsockets_*.dsc
cd libuwebsockets-*/
dpkg-buildpackage -b -us -uc
sudo dpkg -i ../libuwebsockets-dev_*.deb
```

## Package Information

| Field | Value |
|-------|-------|
| **Package** | libuwebsockets-dev |
| **Version** | 20.74.0-1 |
| **Section** | libdevel |
| **Architecture** | all (header-only) |
| **Multi-Arch** | foreign |
| **Maintainer** | Ruslan Dautov |
| **Build-Depends** | debhelper-compat (= 13) |
| **Depends** | libusockets-dev (>= 0.8.8) |

## Debian Packaging Files

```
debian/
├── changelog          # Version history (20.74.0-1)
├── control            # Package metadata and dependencies
├── copyright          # Apache-2.0 license info
├── libuwebsockets-dev.install  # Header files installation
├── rules              # Build instructions
├── source/format      # 3.0 (quilt)
├── watch              # GitHub upstream release tracking
└── tests/
    ├── control              # Autopkgtest configuration
    ├── installation-test    # Verify headers installed
    ├── compilation-test     # Test linking with libusockets
    ├── bloomfilter-test     # BloomFilter unit test
    └── httpparser-test      # HttpParser unit test
```

## Autopkgtest

Package includes comprehensive test suite:

```bash
autopkgtest libuwebsockets-dev_*.deb -- null
```

Tests verify:
- Header file installation (`installation-test`)
- Compilation with libusockets (`compilation-test`)
- BloomFilter functionality (`bloomfilter-test`)
- HttpParser functionality (`httpparser-test`)

## Contributing

1. Fork repository
2. Modify `debian/` directory
3. Update `debian/changelog` with `dch`
4. Test with `dpkg-buildpackage -b -us -uc`
5. Run `lintian` on resulting `.changes` file
6. Submit pull request

## License

- **Upstream**: Apache License 2.0
- **Debian packaging**: Apache License 2.0
- See `debian/copyright` for full details

## Support

- **Packaging issues**: [https://github.com/Fordaxx/uWebSockets-deb/issues](https://github.com/Fordaxx/uWebSockets-deb/issues)
- **Library issues**: [https://github.com/uNetworking/uWebSockets/issues](https://github.com/uNetworking/uWebSockets/issues)

---

**Maintainer**: Ruslan Dautov <r.dautoff2016@yandex.ru>