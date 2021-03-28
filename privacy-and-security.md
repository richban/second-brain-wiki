---
description: Collection of notes and hacks how to enhance your privacy and security.
---

# Privacy & Security

{% hint style="danger" %}
**Problem?** Tracking, surveillance and centralized ecosystems. **Approach?** Compartmentalization. **Goal?** increase privacy and security literacy; reduce fingerprinting; take back control!
{% endhint %}

## 🌍 Browsers

{% hint style="info" %}
Use different browsers and [profiles](https://support.mozilla.org/en-US/kb/dedicated-profiles-firefox-installation#w_what-are-profiles).
{% endhint %}

{% tabs %}
{% tab title="Firefox: Profile 1" %}
**Browser: Firefox**

🔰 Default browser on all devices

🔰 Logged in with a Firefox account in order to sync bookmarks, extensions and tabs

🔰 2 Factor-Authentication Enabled

🔰 Custom config [file](https://ffprofile.com/) to secure the browser even more
{% endtab %}

{% tab title="Firefox: Profile 2" %}
**Browser: Firefox**

🔰 Not user friendly 😉

🔰 Most enhanced settings for privacy and security without relying on any addons with a custom [user.js](https://github.com/arkenfox/user.js/wiki/1.1-Overview) configuration file

**Resource**: [Enhance Your Browser's Privacy & Security with Ghacks/user.js](https://www.youtube.com/watch?v=rkVbsVskqc8&list=PL3cu45aM3C2BwSi8Nj5aBWTrbjbHiXxQo&index=2)
{% endtab %}

{% tab title="Chrome: Profile" %}
**Browser**: Google Chrome

🔰 Used solely for work and accessing Google Cloud Services

🔰 Cookies, search history always cleared after close by default

{% endtab %}
{% endtabs %}

### ⚒️ Extensions

- [**uBlock**](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/): Requires a set of manual custom [configurations](https://www.maketecheasier.com/ultimate-ublock-origin-superusers-guide/) - what domains to block
- [**User-Agent Switcher**](https://gitlab.com/ntninja/user-agent-switcher): spoofs the user agent
- [**Decentraleyes**](https://addons.mozilla.org/en-US/firefox/addon/decentraleyes/): prevents fingerprinting
- [**Privacy Badger**](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/): contains a list of most common trackers which is being updated by default. Unline _uBlock_, does not require custom config
- [**Facebook Container**](https://addons.mozilla.org/en-US/firefox/addon/facebook-container/): prevents Facebook to tracking you
- [**Firefox Multi-Account Containers**]: allows you to use the web with multiple identities or accounts simultaneously

### 🧪 [Test Browser Against Tracking](https://panopticlick.eff.org/) <a id="test-your-browser-against-tracking"></a>

![https://panopticlick.eff.org/](.gitbook/assets/pic_3.png)

- `Do Not Track` - it's fine ✅, we do not want to **unblock** 3rd parties even if they "promise" not to track us - just block them!
- `fingerprinting` user-agent switcher spoofs our fingerprint, so we're good ✅

### 🔍 Search Engines

- [DuckDuckGo](https://duckduckgo.com/) default search engine on all devices

### 🕵🏾♀️ Password Managers

- [1Password](https://1password.com/)
  - Convenient way to store and use passwords
  - Con's: stores your passwords on the cloud and \(might\) expose them to anybody \(hackers, government agencies, etc.\) 😖
- [KeePassXC Password Manager](https://keepassxc.org/)
  - Offline password manager
  - Most secure and Open-source

### 📧 Emails

- [ProtonMail](https://protonmail.com/)

## 💻 Operating System \(darwin\)

{% hint style="danger" %}
[**Your Computer Isn't Yours**](https://sneak.berlin/20201112/your-computer-isnt-yours/):_"your computer serves a remote master, who has decided that they are entitled to spy on you."_
{% endhint %}

### ⚡ Spoof MAC Address

- A MAC address is a unique identifier assigned to your network card
- Each time you connect to a network your MAC address is logged - avoid tracing
- [How to spoof your MAC address and hostname automatically at boot on macOS - Sun Knudsen](https://sunknudsen.com/privacy-guides/how-to-spoof-your-mac-address-and-hostname-automatically-at-boot-on-macos)

{% tabs %}
{% tab title="Spoofs MAC address each time the OS X is rebooted" %}

```bash
# download mac-address-prefixes.txt
curl -o /usr/local/sbin/mac-address-prefixes.txt https://sunknudsen.com/static/media/privacy-guides/how-to-spoof-your-mac-address-and-hostname-automatically-at-boot-on-macos/mac-address-prefixes.txt

# copy to the terminal
cat << "EOF" > /usr/local/sbin/spoof.sh
#! /bin/sh

set -e

export LC_CTYPE=C

basedir=$(dirname "$0")

# Spoof MAC address of en0 interface
mac_address_prefix=`sed "$(jot -r 1 1 768)q;d" $basedir/mac-address-prefixes.txt | sed -e 's/[^A-F0-9:]//g'`
mac_address_suffix=`openssl rand -hex 3 | sed 's/\(..\)/\1:/g; s/.$//'`
mac_address=`echo "$mac_address_prefix:$mac_address_suffix" | awk '{print toupper($0)}'`
sudo ifconfig en0 ether "$mac_address"
printf "%s\n" "Spoofed MAC address of en0 interface to $mac_address"
EOF

# make spoof.sh executable
chmod +x /usr/local/sbin/spoof.sh

# create a local.spoof.plist launch deamon
cat << "EOF" | sudo tee /Library/LaunchDaemons/local.spoof.plist
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>spoof</string>

    <key>ProgramArguments</key>
    <array>
        <string>/usr/local/sbin/spoof.sh</string>
    </array>

    <key>RunAtLoad</key>
    <true/>
  </dict>
</plist>
EOF
```

{% endtab %}
{% endtabs %}

### 🚁 VPN

- ISP is selling your data
- [NordVPN](https://nordvpn.com/) and like - [Don't Trust VPN Providers](https://www.youtube.com/watch?v=qMuYCxxRamc)
- VPN providers might still log your data
- [Mac OS X BigSur Does not bypass VPNS](https://www.reddit.com/r/vim/comments/k0jjqp/understanding_plugin_commands/)

### 👻 Secure your DNS Queries with Encrypted DNS

- [DNS Server](https://www.lifewire.com/what-is-a-dns-server-2625854) is configured and using address space `127.0.0.1` which means it's using the configuration of the router
- By default the router pulls DNS Server from ISP
  - Root of the problem - ISP does not use `encrypted` DNS Server or `qname minimization`
    - **Purpose:** don't send the entire URL to each domain level to resolve the URL
    - `http://www.upenn.edu` → DNS Server → `1.2.3.4`
    - Test whether `qname minimization` is working

```text

dig +short txt qnamemintest.internet.nl
```

![qname minimization](.gitbook/assets/qname.jpg)

### 👨 DNS Providers

- [Encrypted DNS Resolvers \| PrivacyTools](https://www.privacytools.io/providers/dns/)
- [NextDNS](https://my.nextdns.io/b71159/setup)
- [Cloudflare ESNI Checker \| Cloudflare](https://www.cloudflare.com/ssl/encrypted-sni/)

### DNS + VPN

_placeholder_

### 😈 Little Snitch

- makes Internet connections visible to your machine
- application firewall layer

![Little Snitch](.gitbook/assets/snitch.png)

### 🎧 Micro Snitch

- Monitors and reports any microphone and camera activity

### 🔍 Spotlight

- by default everything you type is sent to Apple
- find out yourself: 👉 `sudo tcpdump | grep "api-bos.smoot.apple.com"`
- Dissable in System Prefs -> Spotlight:
  - _Spotlight Suggestions_
  - _Allow Spotlight Suggestions in Look Up_

### 2FA

### SMS

### Signal
