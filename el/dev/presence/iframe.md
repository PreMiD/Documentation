---
title: iFrame Class
description: 
published: true
date: 2021-09-18T14:30:46.924Z
tags: 
editor: markdown
dateCreated: 2021-09-07T01:44:30.059Z
---

# iFrame Class

## Εισαγωγή

In some scenarios, your presence may need to access elements inside of `iframes`.

The code that you write inside of your `iframe.ts` file gets injected into every iframe on the page.

Like presences, `iframes` have their own classes designed to automatically update data.

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Code goes here...
});
```

## Μέθοδοι

### `send(Object)`
Sends data to the presence. Using this method will make the presence throw a `iFrameData` event.

### `getUrl()`
Returns the URL of the `iframe`.

## Events
In `iframes`, events work similarly to the way they work in the `presence` class.

```typescript
iframe.on("UpdateData", async () => {
    // Code goes here...
});
```

Here is a list of all of the events:

#### `UpdateData`

This event is fired every time the iframe is being updated.
