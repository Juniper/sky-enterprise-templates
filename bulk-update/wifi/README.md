# SRX WiFi Feature

Using the new WiFi mPIM for SRX https://www.juniper.net/documentation/en_US/release-independent/junos/topics/topic-map/srx-series-wifi-mpim.html

## Templates
 
### srx-wifi

This template used Junos stanza and can be loaded using the bulk updates merge tool. The configuration creates a trusted and a guest network. The trusted network includes wired (via irb) and wireless network clients, the guest network is wireless only.

### srx-wifi-variables-set

Example of a simple wlan config for SRX
