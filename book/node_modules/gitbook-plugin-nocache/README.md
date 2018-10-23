# gitbook-plugin-nocache

[![npm](https://img.shields.io/npm/v/gitbook-plugin-nocache.svg)](https://www.npmjs.com/package/gitbook-plugin-nocache)
[![npm](https://img.shields.io/npm/dt/gitbook-plugin-nocache.svg)](https://www.npmjs.com/package/gitbook-plugin-nocache)
[![npm](https://img.shields.io/npm/l/gitbook-plugin-nocache.svg)](https://www.npmjs.com/package/gitbook-plugin-nocache)

Disable page cache for your [gitbook](https://www.gitbook.com/).

## Config

In your book.json, add this plugin:

```javascript
{
    "plugins": [
        "nocache"
    ]
}
```

Then you will see the meta tags in the `<head>` section of your book.