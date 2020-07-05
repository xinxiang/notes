# OpenVPN 2.4 on Windows

I have a .ovpn file for me to connect to my University. However, when I tried to use it on Windows 10 with OpenVpn 2.4.9 (almost the latest). I got two errors. The first one is easy to fix, but the second one requires to regenerate the keys. Since it is a legacy service, there is no longer new keys can be generated. So I have to keep using OpenVPN 2.3 (up to 2.3.18).

## error 1: Unrecognized option or missing or extra parameter(s) in client.ovpn:130: tls-remote (2.4.6)
**Fix**: replace the line with 

```
verify-x509-name vpnsever.domain name
```

**Ref**: https://superuser.com/questions/1405659/openvpn-options-error-unrecognized-option-or-missing-or-extra-parameters-in

## error 2: OpenVPN 'SSL_CTX_use_certificate:ca md too weak'

**Fix**: I tried both solutions suggested in the doc below - modify *openssl.conf* and *DEFAULT:@SECLEVEL=0*; but neither worked for me.

**Ref**: https://www.infopackets.com/news/10414/how-fix-openvpn-sslctxusecertificateca-md-too-weak

## Download OpenVPN
* https://openvpn.net/community-downloads/
* https://build.openvpn.net/downloads/releases/

# VPN over VPN
On Mac, with Tunnelblick, I can connect to VPN1 and then connect to VPN2 to access resources required two different VPNs; but on Windows with OpenVPN, I can't.
