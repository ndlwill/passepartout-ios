<p style="text-align: center; padding: 2em"><img src="res/logo.png" /></p>

# [Passepartout][about-website]

![iOS 11+](https://img.shields.io/badge/ios-11+-green.svg)
[![TunnelKit 1.1.x](https://img.shields.io/badge/tunnelkit-1.1-d69c68.svg)][dep-tunnelkit]
[![License GPLv3](https://img.shields.io/badge/license-GPLv3-lightgray.svg)](LICENSE)
[![Join TestFlight](https://img.shields.io/badge/beta-TestFlight-5ecdf6.svg)][about-testflight]
[![Join Reddit](https://img.shields.io/badge/discuss-Reddit-orange.svg)][about-reddit]
[![Join Telegram](https://img.shields.io/badge/chat-Telegram-blue.svg)][about-telegram]
[![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?url=https%3A%2F%2Fpassepartoutvpn.app%2F&via=keeshux&text=Passepartout%20is%20an%20user-friendly%2C%20open%20source%20%23OpenVPN%20client%20for%20%23iOS%20and%20%23macOS)
 
Passepartout is a non-official, user-friendly [OpenVPN®][openvpn] client for iOS.

## Beta

Passepartout is in [public beta][about-testflight] on TestFlight.

<a href="https://www.patreon.com/keeshux"><img src="https://c5.patreon.com/external/logo/become_a_patron_button@2x.png" width="160"></a>

By using a beta version of the app, you understand that the software might be unstable, unreliable or plain broken from time to time.

## Overview

### All profiles in one place

Passepartout lets you handle multiple profiles in one single place and quickly switch between them.

[<img src="res/snap-home.png" width="300">](res/snap-home.png)

### Ease of use

With its native look & feel, Passepartout focuses on ease of use. It does so by stripping the .ovpn flags that are today obsolete or rarely used. With good approximation, it mimics the most relevant features you will find in OpenVPN 2.4.x.

[<img src="res/snap-profile.png" width="300">](res/snap-profile.png)

### Trusted networks

Trust cellular or Wi-Fi networks to fine-grain your connectivity. You can then choose to retain a VPN connection when entering a trusted network, or prevent it completely.

[<img src="res/snap-trusted.png" width="300">](res/snap-trusted.png)

### See your connection parameters

Passepartout strives for transparency, by showing a fairly detailed yet understandable resume of your connection parameters.

[<img src="res/snap-parameters.png" width="300">](res/snap-parameters.png)

### Disconnect on sleep

Keeping the VPN active in the background provides smoother operation, but may be tough for the battery. You might want to use this feature if you're concerned about battery life. When the device goes to sleep, the VPN will disconnect to then reconnect on device wake-up.

### No unrequested activity

Passepartout is a VPN client and does absolutely nothing else without your consent. The providers infrastructures are obtained via a [static GitHub API][app-api] if and only if you manually refresh them.

### Presets for major providers

Passepartout can connect to a few well-known VPN providers with an existing account:

- [Private Internet Access][app-net-pia]
- ...more soon!

In preset mode, you can pick pre-resolved IPv4 endpoints when DNS is problematic.

### Import .ovpn profiles

Passepartout can import .ovpn configuration files. This way you can fine-tune encryption without tweaking and reimporting a new configuration. Below are a few limitations worth mentioning.

Unsupported:

- UDP fragmentation, i.e. `--fragment`
- Compression
    - `--comp-lzo` other than `no`
    - `--compress` other than empty
- Proxy
- External file references (inline `<block>` only)
- Encrypted certificate private key (will raise error TunnelKitNative Code=205)

Ignored:

- MTU overrides
    - `--*-mtu` and variants
    - `--mssfix`
- Multiple `--remote` with different `host` values (first wins)

Many other flags are ignored too but it's normally not an issue.

## Installation

### Requirements

- iOS 11.0+
- Xcode 10+ (Swift 4.2)
- Git (preinstalled with Xcode Command Line Tools)
- Ruby (preinstalled with macOS)
- [CocoaPods 1.4.0][dep-cocoapods]

It's highly recommended to use the Git and Ruby packages provided by [Homebrew][dep-brew].

### Testing

Download the app codebase locally:

    $ git clone https://github.com/keeshux/passepartout-ios.git

Assuming you have a [working CocoaPods environment][dep-cocoapods], setting up the app workspace only requires installing the pod dependencies:

    $ pod install

After that, open `Passepartout.xcworkspace` in Xcode and run the `Passepartout-iOS` target.

For the VPN to work properly, the app requires:

- _App Groups_ and _Keychain Sharing_ capabilities
- App IDs with _Packet Tunnel_ entitlements

both in the main app and the tunnel extension target.

## License

This project is licensed under the [GPLv3][license-content].

### Contributing

By contributing to this project you are agreeing to the terms stated in the [Contributor License Agreement (CLA)][contrib-cla]. For more details please see [CONTRIBUTING][contrib-readme].

## Credits

The logo is taken from the awesome Circle Icons set by Nick Roach.

- SwiftyBeaver - © 2015 Sebastian Kreutzberger
- MBProgressHUD - © 2009-2016 Matej Bukovinski

© 2002-2018 OpenVPN Inc. - OpenVPN is a registered trademark of OpenVPN Inc.

## Disclaimer

Passepartout is a VPN client based on independent work. As such, the developer -while making his best efforts to avoid it- takes no responsibility about any damage caused by the use of this software.

Additionally, the developer takes no responsibility about data usage, monitoring, logging etc. by the servers you connect to. Passepartout is not even involved in the above choices, as they're part of server-side policies.

For more information about data usage by third parties, please review the privacy policy of your VPN provider.

## Contacts

Twitter: [@keeshux][about-twitter]

Website: [passepartoutvpn.app][about-website]

[openvpn]: https://openvpn.net/index.php/open-source/overview.html

[app-api]: https://github.com/keeshux/passepartout-api
[app-net-pia]: https://www.privateinternetaccess.com

[dep-cocoapods]: https://guides.cocoapods.org/using/getting-started.html
[dep-jazzy]: https://github.com/realm/jazzy
[dep-brew]: https://brew.sh/
[dep-tunnelkit]: https://github.com/keeshux/tunnelkit
[dep-openssl]: https://www.openssl.org/

[license-content]: LICENSE
[contrib-cla]: CLA.rst
[contrib-readme]: CONTRIBUTING.md

[about-twitter]: https://twitter.com/keeshux
[about-website]: https://passepartoutvpn.app
[about-patreon]: https://www.patreon.com/keeshux
[about-testflight]: https://testflight.apple.com/join/XHzgXj6m
[about-reddit]: https://www.reddit.com/r/passepartout
[about-telegram]: https://t.me/passepartoutvpn
