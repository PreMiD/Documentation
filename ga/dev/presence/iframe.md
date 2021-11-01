---
title: Rang iFrame
description:
published: true
date: 2021-09-18T14:31:12.831Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# Rang iFrame

## Réamhrá

I roinnt cásanna, b’fhéidir go mbeidh ar do presence rochtain a fháil ar eilimintí taobh istigh de` iframes`.

Déantar an cód a scríobhann tú taobh istigh de do `iframe.ts` chomhad a instealladh i ngach iframe ar an leathanach.

Cosúil le presences, `iframes` tá a gcuid ranganna féin deartha chun sonraí a nuashonrú go huathoibríoch.

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Cód anseo.
});
```

## Modhanna

### `send(Object)`
Seolann sé sonraí chuig an presence. Trí úsáid a bhaint as an modh seo, caithfear an presence a chaitheamh `iFrameData`.

### `getUrl()`
Filleann sé URL an `iframe`.

## Imeachtaí
In `iframes`, oibríonn imeachtaí ar an gcaoi chéanna leis an mbealach a oibríonn siad sa `presence` rang.

```typescript
iframe.on("UpdateData", async () => {
    // Cód anseo
});
```

Seo liosta de na himeachtaí ar fad:

#### `UpdateData`

Scaoiltear an t-imeacht seo gach uair a dhéantar an iframe a nuashonrú.
