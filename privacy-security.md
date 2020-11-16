# Privacy & Security

---

## **Problem?** Tracking, surveillance and centralized ecosystems. Companies track all our movements online, every click, every key stroke is being loggged and sent to remote servers. I refuse to accept that I am constantly monitored without any consent, I want to know what/how/why/when is being sent to remote servers. **Approach?** Compartmentalization,

# Browsers

- Different browsers and profiles for different use cases.

## Firefox

- I have different profiles for private, work or other browsing and I think you should have too 😉
- Default browser on all devices

### Profile #1 Private

- A profile mainly for private browsing (github, stackoverflow, twitter, etc.)
- A Firefox logged in account with email address so my history and bookmarks are synced across devices.
- 2 Factor Authentication enabled
- Do not store any passwords in Firefox use a password manager instead
- Custom configuration file`user.js` based on YouTuber: Mental Outlaw

  ```jsx
  /**
   * Maximize Firefox Browser Privacy and Security
   * Based on: https://www.youtube.com/watch?v=xxWXLlfqNAo&list=PL3cu45aM3C2BwSi8Nj5aBWTrbjbHiXxQo&index=1
   * Mental Outlaw ***/

  // WebRTC can give up your real IP even when using VPN or Tor
  user_pref("media.peerconnection.enabled", false);
  /*** Enable fingerprint resistance:  With this alone we pretty much
   * negate the need for canvas defender, or any other fingerprint blocking addon
   * ***/
  user_pref("privacy.resistfingerprinting", true);
  // 3DES has known security flaws
  user_pref("security.ssl3.rsa_des_ede3_sha", false);
  // Require Safe Negotiation:  Optimize SSL
  user_pref("security.ssl.require_safe_negotiation", true);
  // Disable TLS 1.0, 1.1
  user_pref("security.tls.version.min", 3);
  // enables TLS 1.3
  user_pref("tls.version.max", 4);
  // Disable 0 round trip time to better secure your forward secrecy
  user_pref("security.tls.enable_0rtt_data", false);
  // Disable Automatic Formfill
  user_pref("browser.formfil.enable", false);
  // Disable disk caching
  user_pref("browser.cache.disk.enable", false);
  user_pref("browser.cache.disk_cache_ssl", false);
  user_pref("browser.cache.memory.enable", false);
  user_pref("browser.cache.offline.enable", false);
  user_pref("browser.cache.insecure.enable", false);
  // Disable geolocation services
  user_pref("geo.enabled", false);
  // Disable plugin scanning.
  user_pref("plugin.scan.plid.all", false);
  // Disable ALL telemetery
  user_pref(
    "browser.newtabpage.activity-stream.feeds.telemetry browser.newtabpage.activity-stream.telemetry",
    false
  );
  user_pref("browser.pingcentre.telemetry", false);
  user_pref("devtools.onboarding.telemetry-logged", false);
  user_pref("media.wmf.deblacklisting-for-telemetry-in-gpu-process", false);
  user_pref("toolkit.telemetry.archive.enabled", false);
  user_pref("toolkit.telemetry.bhrping.enabled", false);
  user_pref("toolkit.telemetry.firstshutdownping.enabled", false);
  user_pref("toolkit.telemetry.hybridcontent.enabled", false);
  user_pref("toolkit.telemetry.newprofileping.enabled", false);
  user_pref("toolkit.telemetry.unified", false);
  user_pref("toolkit.telemetry.updateping.enabled", false);
  user_pref("toolkit.telemetry.shutdownpingsender.enabled", false);
  // Allows direct access to GPU.
  user_pref("webgl.disabled", true);
  /*
   * Enable first-party isolation. Prevents browsers from making requests
   * outside of the primary domain of the website. Prevents supercookies.
   * may cause websites that rely on 3rd party scripts and libraries to break,
   * however those are generally only used for tracking so fuck them anyway. **/
  user_pref("privacy.firstparty.isolate", true);
  // Disable TLS false start
  user_pref("security.ssl.enable_false_start", false);
  ```

- Added this file `user.js` to the root folder of my Firefox profile, the path is something like → `/Firefox/Profiles/50agk1qv.default/user.js` or manually change settings in `about:config`
- What is it, what does it do, and why would I want one?

  [arkenfox/user.js](https://github.com/arkenfox/user.js/wiki/1.1-Overview)

[Maximize Your Browsers Privacy and Security with ZERO ADDONS!!!](https://www.youtube.com/watch?v=xxWXLlfqNAo&t=203s)

### Extensions

- If you can't be bothered with locating configurations files or setting them manually in Firefox `about:config`, the following `addons` are excellent choice.
- I use bellow `addons` and the custom `user.js` config file from above as well
- **Ublock Origin Extension**

  - Wide-spectrum content blocker
  - Requires set of manual custom configurations - what domains to block.

  [uBlock Origin - Get this Extension for 🦊 Firefox (en-US)](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)

  ### Minimum Settings

  ![Privacy%20&%20Security%209223091161b048919970afb16f624c67/Screen_Shot_2020-10-10_at_10.03.17_AM.png](Privacy%20&%20Security%209223091161b048919970afb16f624c67/Screen_Shot_2020-10-10_at_10.03.17_AM.png)

  ### Guide to uBlock Origin

  [The Ultimate Superuser's Guide to uBlock Origin - Make Tech Easier](https://www.maketecheasier.com/ultimate-ublock-origin-superusers-guide/)

  ### Resource

  [Three Fast and Simple Ways to Enhance Your Browsers Privacy and Security.](https://youtu.be/n0kl6t7U7K4?t=339)

- **Privacy Badger**

  - No custom configuration needed
  - Privacy Badger allready contains a list of most common trackers which is being updated by default

  [Privacy Badger - Get this Extension for 🦊 Firefox (en-US)](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/)

- **Decentraleyes**

  - Preventes fingerprinting
  - Con's -

  [Decentraleyes - Get this Extension for 🦊 Firefox (en-US)](https://addons.mozilla.org/en-US/firefox/addon/decentraleyes/)

- **User-Agent Switcher**

  - Spoofs the User-agent

  [User-Agent Switcher - Get this Extension for 🦊 Firefox (en-US)](https://addons.mozilla.org/en-US/firefox/addon/uaswitcher/)

## Profile #2 Maximum Privacy

- `Ghacks/user.js`
- Defines the most enhanced settings for privacy and security without relying on any addons
- Copy and paste the `user.js` profile into the Firefox root profile folder `/Firefox/Profiles/50agk1qv.default/user.js`
- Not recommending for the average user 🙂 I only went trough the bare minimum...: [https://github.com/arkenfox/user.js/wiki/1.3-Implementation](https://github.com/arkenfox/user.js/wiki/1.3-Implementation)
- Also defined some `custom-overrides.js`
- Dev's at Mozilla are thinking to deprecating the `user.js`

[arkenfox/user.js](https://github.com/arkenfox/user.js)

[Enhance Your Browser's Privacy & Security with Ghacks/user.js](https://www.youtube.com/watch?v=rkVbsVskqc8&list=PL3cu45aM3C2BwSi8Nj5aBWTrbjbHiXxQo&index=2)

## Chrome

- I still sometimes use chrome for convenience by try to limit my usage
- Mostly using Chrome for Google Cloud Services like GCP
- Using different profiles for different purposes
- Installed with above extensions

### Safari

- Does not prevent well from tracking
- Example: Default Safari Settings

  ![Privacy%20&%20Security%209223091161b048919970afb16f624c67/Screen_Shot_2020-10-10_at_1.26.11_PM.png](Privacy%20&%20Security%209223091161b048919970afb16f624c67/Screen_Shot_2020-10-10_at_1.26.11_PM.png)

## Test Your Browser Against Tracking

[Panopticlick](https://panopticlick.eff.org/)

![Privacy%20&%20Security%209223091161b048919970afb16f624c67/Screen_Shot_2020-10-10_at_12.29.01_PM.png](Privacy%20&%20Security%209223091161b048919970afb16f624c67/Screen_Shot_2020-10-10_at_12.29.01_PM.png)

- `Do Not Track` - it's fine ✅, we do not want to **unblock** 3rd parties even if they "promise" not to track us - just block them!
- `fingerprinting` user-agent switcher spoofs our fingerprint, so we're good ✅

# Search Engines

### DuckDuckGo

- Default search engine on all devices

[DuckDuckGo - Privacy, simplified.](https://duckduckgo.com/)

### Startpage.com

- Obviously: _"You can’t beat Google when it comes to online search."_ but there are ways how you can get answers and still get rid of trackers and logs
- It utilizes Google Search but removes trackers and logs

[Startpage.com - The world's most private search engine](https://startpage.com/)

# Password Managers

---

### 1Password

- Easiest way to store and use passwords
- Installed on all devices
- Drawback - stores your passwords online and exposes them to anybody (hackers, government agencies, etc.)

[Password Manager for Families, Businesses, Teams | 1Password](https://1password.com/)

### KeePassXC

- Offline password manager
- Most secure
- Open-source

[KeePassXC Password Manager](https://keepassxc.org/)

# Spoof MAC address

---

- A MAC address is a unique identifier assigned to your network card
- Each time you connect to a network your MAC address is logged - avoid tracing
- Spoofs MAC address each time the OS X is rebooted

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

### Source

[How to spoof your MAC address and hostname automatically at boot on macOS - Sun Knudsen](https://sunknudsen.com/privacy-guides/how-to-spoof-your-mac-address-and-hostname-automatically-at-boot-on-macos)

# VPN

---

- Your ISP sells your data 😉
- Good price

[NordVPN: Best VPN Service Provider | #1 Editors' Choice](https://nordvpn.com/)

# Secure your DNS Queries with Encrypted DNS

---

- DNS Server is configured and using address space `127.0.0.1` which means it's using the configs of your router
- By default your router pulls DNS Server from your ISP
  - Root of the problem - ISP does not use `encrypted` DNS Server or `qname minimization`
  - Don't send the entire URL to each domain level to resolve the URL
  - `[www.upenn.edu](http://www.upenn.edu)` → DNS Server → `1.2.3.4`

![Privacy%20&%20Security%209223091161b048919970afb16f624c67/qname.jpg](Privacy%20&%20Security%209223091161b048919970afb16f624c67/qname.jpg)

qname minimization

- Request drawings.tumblr.com.de → DNS Root
  - .de - where is .de? German Servers
  - .com - .de → has to ask .com top level domain with the full URL
  - .com → has to ask tumblr
- With `qname minimization`:
  - they don't ask a `drawings.tumblr`

### Encrypted DNS Resolvers

[Encrypted DNS Resolvers | PrivacyTools](https://www.privacytools.io/providers/dns/)

[NextDNS](https://my.nextdns.io/b71159/setup)

[Cloudflare ESNI Checker | Cloudflare](https://www.cloudflare.com/ssl/encrypted-sni/)

```bash
# test whether qname minimization is working
dig +short txt qnamemintest.internet.nl

\# "HOORAY - QNAME minimisation is enabled on your resolver :)!"
```

# 3rd Party Cookies

---
