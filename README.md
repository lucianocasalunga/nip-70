# NIP-70 · Protected Events on LiberNet

> Protected Events, as used by the **LiberNet** apps.

**Official spec:** [nostr-protocol/nips · 70.md](https://github.com/nostr-protocol/nips/blob/master/70.md)
**Status upstream:** `draft` `optional` `relay`
**Maintainer of this repo:** Luciano "Barak" Casalunga ([@lucianocasalunga](https://github.com/lucianocasalunga)) · [libernet.app](https://libernet.app)

## My role

I took part in the creation of NIP-70, and it runs across the LiberNet apps.

## Why NIP-70 matters for LiberNet

LiberNet is a community. NIP-70 lets an author mark an event with `["-"]` so only the author can publish it, after authenticating. Community posts stay where they were meant to be instead of being copied to every relay.

## How it works (quick reference)

| Element | Purpose |
|---------|---------|
| `["-"]` tag | Marks the event as protected |
| NIP-42 `AUTH` | Relay checks the publisher is the author |
| `auth-required:` | Relay asks the client to authenticate first |

Default relay behaviour: reject any event with `["-"]` unless the authenticated pubkey is the author. LiberNet announces `70` in its NIP-11 `supported_nips`.

### Flow on LiberNet

```
client                          LiberNet relay
  |-- EVENT {tags: [["-"]]} ----->|
  |<-- AUTH <challenge> ----------|
  |<-- OK false "auth-required: …"|
  |-- AUTH {signed} ------------->|
  |-- EVENT {tags: [["-"]]} ----->|
  |<-- OK true -------------------|
```

## Related LiberNet NIPs

[NIP-43](https://github.com/lucianocasalunga/nip-43) · [NIP-45](https://github.com/lucianocasalunga/nip-45) · [NIP-50](https://github.com/lucianocasalunga/nip-50) · [NIP-66](https://github.com/lucianocasalunga/nip-66) · [NIP-67](https://github.com/lucianocasalunga/nip-67) · [NIP-77](https://github.com/lucianocasalunga/nip-77) · [NIP-86](https://github.com/lucianocasalunga/nip-86) · [NIP-95 (my proposal)](https://github.com/lucianocasalunga/nip-95)

---
Nostr since 2021 · Part of the LiberNet ecosystem
