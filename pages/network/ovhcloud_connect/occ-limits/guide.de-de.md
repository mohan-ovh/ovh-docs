---
title: Technical capabilities and limitations
excerpt: 'Learn the technical capabilities and limitations of the OVHcloud Connect solution'
updated: 2022-08-25
routes:
    canonical: 'https://help.ovhcloud.com/csm/en-gb-network-ovhcloud-connect-limits?id=kb_article_view&sysparm_article=KB0045259'
---

## Objective

**This page provides an overview of the technical capabilities and limitations of the OVHcloud Connect solution.**

## Instructions

### Link capabilities

- 1000Base-LX/LH for 1Gb
- 10GBase-LR for 10Gb
- Jumbo frame up to 9000 bytes
- Autonegotiation not supported

### Technical limitationss

#### Layer 2 mode

- The number of client-side MAC addresses is limited to 512 per port

#### Layer 3 mode

- Each EntryPoint/POP supports only one BGP session (no eBGP Multihop)
- Each EndPoint/DC supports up to 4 BGP peers
- Up to 100 prefixes can be announced per BGP session

### Unsupported features

#### Layer 2 mode

- 802.1p CoS-based
- DCBX and related protocols (802.1Qbb, 802.1Qaz, 802.1Qau)
- TRILL, SPF and FabricPath
- FCoE
- Spannning-tree
- IGMP and Multicast
- EtherChannel, PaGP for aggregation

#### Layer 3 mode

- IPv6
- Any QoS mechanism
- 802.1q tag
- Multi-VRF
- eBGP Multi-Hop
- iBGP
- Static routing in EntryPoint/PoP

### Known issues

| Description | Detail | Cause | Workaround | Affected sites |
|:-----:|:------:|:-----:|:----------:|:--------------:|
| DC routes not propagated to PoP | When using AS65501, routes announced using BGP in vRack are not propagated to PoP | OVHcloud internal configuration | Do not use AS65501 | ALL |
| Light received but port is down | Device fails to change interface status to UP despite optical levels on RX are correct | Autonegotiation is configured | Unconfigure autonegotiation | ALL PoPs |

## Go further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/de/professional-services/) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our community of users on <https://community.ovh.com/en/>.
