---
title: "RTCIceCandidateStats: protocol property"
short-title: protocol
slug: Web/API/RTCIceCandidateStats/protocol
page-type: web-api-instance-property
browser-compat: api.RTCStatsReport.type_local-candidate.protocol
---

{{APIRef("WebRTC")}}

The **`protocol`** property of the {{domxref("RTCIceCandidateStats")}} dictionary indicates the protocol the specified candidate would use for communication with the remote peer.

## Value

The value is one of the following strings:

- `tcp`
  - : The candidate, if selected, would use {{Glossary("TCP")}} as the transport protocol for its data.
    The {{domxref("RTCIceCandidate.tcpType", "tcpType")}} property provides additional information about the kind of TCP candidate represented by the object.
- `udp`
  - : The candidate will use the {{Glossary("UDP")}} transport protocol for its data.
    This is the preferred protocol for media interactions because of its better performance profile.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
