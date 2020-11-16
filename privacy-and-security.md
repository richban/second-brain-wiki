---
description: Collection of notes and hacks how to secure your privacy and security.
---

# Privacy & Security

{% hint style="danger" %}
**Problem?** Tracking, surveillance and centralized ecosystems. **Approach?** 
{% endhint %}

## Browsers

{% hint style="info" %}
Use different browsers and [profiles](https://support.mozilla.org/en-US/kb/dedicated-profiles-firefox-installation#w_what-are-profiles) for different use cases. Below is my personal set up.
{% endhint %}

{% tabs %}
{% tab title="Firefox: Profile 1" %}
 **Browser: Firefox**

Used for personal but not sensitive browsing

Logged in with a Firefox account in order to sync tabs and bookmarks

2 Factor-Authentication Enabled

Custom config file to secure the browser even more.
{% endtab %}

{% tab title="Firefox: Profile 2" %}
**Browser: Firefox**

Used to overthrown governments

Most enhanced settings for privacy and security without relying on any addons with a custom [user.js](https://github.com/arkenfox/user.js/wiki/1.1-Overview) configuration file

**Resource**: [Enhance Your Browser's Privacy & Security with Ghacks/user.js](https://www.youtube.com/watch?v=rkVbsVskqc8&list=PL3cu45aM3C2BwSi8Nj5aBWTrbjbHiXxQo&index=2)
{% endtab %}

{% tab title="Brave: Profile" %}
**Browser**: Brave Browser

Used mostly for convenience when Firefox breaks
{% endtab %}

{% tab title="Chrome: Profile" %}
**Browser**: Google Chrome

Used solely for work and accessing Google Cloud Services
{% endtab %}
{% endtabs %}

### Extensions

* \*\*\*\*[**uBlock**](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)**:** wide-spectrum content blocker. Requires set of manual custom configurations. Requires a set of manual custom [configurations](https://www.maketecheasier.com/ultimate-ublock-origin-superusers-guide/) - what domains to block.
* \*\*\*\*[**User-Agent Switcher**](https://gitlab.com/ntninja/user-agent-switcher)**:** spoofs the user agent.
* \*\*\*\*[**Decentraleyes**](https://addons.mozilla.org/en-US/firefox/addon/decentraleyes/)**:** prevents finger printing.
* [**Privacy Badger**](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/)**:** contains a list of most common trackers which is being updated by default.
* \*\*\*\*[**Facebook Container**](https://addons.mozilla.org/en-US/firefox/addon/facebook-container/): prevents FB to tracking you.

### Test Your Browser Against Tracking <a id="test-your-browser-against-tracking"></a>

* `Do Not Track` - it's fine ✅, we do not want to **unblock** 3rd parties even if they "promise" not to track us - just block them!
* `fingerprinting` user-agent switcher spoofs our fingerprint, so we're good ✅



