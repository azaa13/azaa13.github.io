---
layout: post
title:  "Why need to revoke object url after creating obj URL Blob or other objects? "
date:   2020-03-02 16:37:00 +0900
categories: dom revokeURL best-practice
---

As we use File, Blob other other media related objects to display them in web page. Generally `createObjectURL` is used to fulfill this task. Indeed this is very useful as it generated DOMstring containing a url to represent object.

The lifetime of the URL is attached to the `document` in the window, hence until the window is closed or redirected to any other route the URL still accessible.

```js
<template>
    <img :src=blobURL alt="">
</template>

blobObj:Blob = null
blobURL = window.URL.createObjectURL(blobObj)

// blobURL can be used as any File/Media source obj.
```

## Best practice for memory management

As its validity is quite longer, manually can release the object URL using `revokeObjectURL()`.

Even though browser will release the object URL automatically when the window is cleared, but it is still highly advised to revoke its URL by ourselves as well, for optimizing performance and efficient memory usage.

```js
<template>
    <img :src=blobURL alt="">
</template>

blobObj:Blob = null
blobURL = window.URL.createObjectURL(blobObj)

// to release or free the object URL

window.URL.createObjectURL(blobObj)

// blobURL can be used as any File/Media source obj.
```

For more detailed info, please visit <https://developer.mozilla.org/en-US/docs/Web/API/URL/createObjectURL>.