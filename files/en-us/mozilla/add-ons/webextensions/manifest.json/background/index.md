---
title: background
slug: Mozilla/Add-ons/WebExtensions/manifest.json/background
page-type: webextension-manifest-key
browser-compat: webextensions.manifest.background
sidebar: addonsidebar
---

<table class="fullwidth-table standard-table">
  <tbody>
    <tr>
      <th scope="row">Type</th>
      <td><code>Object</code></td>
    </tr>
    <tr>
      <th scope="row">Mandatory</th>
      <td>No</td>
    </tr>
    <tr>
      <th scope="row">Manifest version</th>
      <td>2 or higher</td>
    </tr>
    <tr>
      <th scope="row">Example</th>
      <td>
        <pre class="brush: json">
"background": {
  "scripts": ["background.js"]
}</pre
        >
      </td>
    </tr>
  </tbody>
</table>

Use the `background` key to include one or more background scripts, a background page, or a Service worker in your extension.

Background scripts are the place to put code that needs to maintain a long-term state or perform long-term operations independently of the lifetime of any particular web pages or browser windows.

Background scripts are loaded as soon as the extension is loaded and stay loaded until the extension is disabled or uninstalled unless `persistent` is specified as `false`. You can use any WebExtension APIs in the script if you have requested the necessary [permissions](/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/permissions).

See [Background scripts](/en-US/docs/Mozilla/Add-ons/WebExtensions/Background_scripts) for some more details.

The `background` key is an object that must have one of these properties (for more information on how these properties are supported, see [Browser support](#browser_support)):

<table class="standard-table">
  <tbody>
    <tr>
      <td><code>page</code></td>
      <td>
        <p>
          If you need specific content in the background page, you can define a
          page using the <code>page</code> property. This is a
          <code>string</code> representing a path relative to the manifest.json
          file to an HTML document included in your extension bundle.
        </p>
        <p>
          If you use this property, you can not specify background scripts using
          <code>scripts</code>, but you can include scripts from the
          page, just like a normal web page.
        </p>
      </td>
    </tr>
    <tr>
      <td><code>scripts</code></td>
      <td>
        <p>
          An <code>array</code> of <code>string</code>, each of which is a path
          to a JavaScript source. The path is relative to the manifest.json file
          itself. These are the scripts that are executed in the
          extension's background context.
        </p>
        <p>The scripts share the same <code>window</code> global context.</p>
        <p>The scripts are loaded in the order they appear in the array.</p>
        <p>
          If you specify <code>scripts</code>, an empty page
          is created where your scripts run.
        </p>
        <div class="note">
          <p>
            <strong>Note:</strong> If you want to fetch a script from a remote
            location with the <code>&#x3C;script></code> tag (e.g.,
            <code
              >&#x3C;script src =
              "https://code.jquery.com/jquery-3.6.0.min.js"></code
            >), you have to change the
            <code
              ><a
                href="/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/content_security_policy"
                >content_security_policy</a
              ></code
            >
            key in the manifest.json file of your extension.
          </p>
        </div>
      </td>
    </tr>
    <tr>
      <td><code>service_worker</code></td>
      <td>
        <p>
          Specify a JavaScript file as the extension <a href="/en-US/docs/Web/API/Service_Worker_API">service worker</a>. A service worker is a background script that acts as the extension's main event handler.
        </p>
      </td>
    </tr>
  </tbody>
</table>

The `background` key can also contain this optional property:

<table class="standard-table">
  <tbody>
    <tr>
      <td><code>persistent</code></td>
      <td>
        <p>A <code>boolean</code> value.</p>
        <p>If omitted, this property defaults to <code>true</code> in Manifest V2 and <code>false</code> in Manifest V3. Setting to <code>true</code> in Manifest V3 results in an error.</p>
        <ul>
          <li>
            <code>true</code> indicates the background page is to be kept in
            memory from when the extension is loaded or the browser starts until
            the extension is unloaded or disabled, or the browser is closed
            (that is, the background page is persistent).
          </li>
          <li>
            <code>false</code> indicates the background page may be unloaded
            from memory when idle and recreated when needed. Such background
            pages are often called Event Pages, because they are loaded into
            memory to allow the background page to handle the events to which it
            has added listeners. Registration of listeners is persistent when
            the page is unloaded from memory, but other values are not
            persistent. If you want to store data persistently in an event page,
            then you should use the
            <a href="/en-US/docs/Mozilla/Add-ons/WebExtensions/API/storage"
              >storage API</a
            >.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>preferred_environment</code></td>
      <td>
        <p>An <code>array</code> of <code>string</code> listing the preferred environments in order of precedence.</p>
        <p>If <code>background</code> specifies a <code>service_worker</code> and a <code>page</code> or <code>scripts</code>, this property enables the extension to tell the browser which background context to use if available. See <a href="#browser_support">Browser support</a> for details of the environments supported in the major browsers.</p>
        <ul>
          <li>
            <code>document</code> requests that the browser use the extension's background scripts as documents, if supported.
          </li>
          <li>
            <code>service_worker</code> requests that the browser run the extension's background scripts as service workers, if supported.
          </li>
        </ul>
        <p>Chrome only supports service workers, so it ignores this key. If omitted, Firefox and Safari run background scripts as documents. Safari uses a service worker context if the extension specifies <code>scripts</code> and <code>preferred_environment</code> is set to <code>service_worker</code>.</p>
      </td>
    </tr>
    <tr>
      <td><code>type</code></td>
      <td>
        <p>A <code>string</code> value.</p>
        <p>Determines whether the scripts specified in <code>scripts</code> are loaded as ES modules.</p>
        <ul>
          <li>
            <code>classic</code> indicates the background scripts or service workers are not included as an ES Module.
          </li>
          <li>
            <code>module</code> indicates the background scripts or service workers are included as an ES Module. This enables the background page or service worker to <code>import</code> code.
          </li>
        </ul>
        <p>If omitted, this property defaults to <code>classic</code>.</p>
      </td>
    </tr>
  </tbody>
</table>

## Browser support

Support for the `scripts`, `page`, and `service_worker` properties varies between browsers like this:

- Chrome:
  - supports `background.service_worker`.
  - supports `background.scripts` (and `background.page`) in Manifest V2 extensions only.
  - before Chrome 121, Chrome refuses to load a Manifest V3 extension with `background.scripts` or `background.page` present. From Chrome 121, their presence in a Manifest V3 extension is ignored.
- Firefox:
  - `background.service_worker` is not supported (see [Firefox bug 1573659](https://bugzil.la/1573659)).
  - supports `background.scripts` (or `background.page`) if `service_worker` is not specified or the service worker feature is disabled. Before Firefox 120, Firefox did not start the background page if `service_worker` was present (see [Firefox bug 1860304](https://bugzil.la/1860304)). From Firefox 121, the background page starts as expected, regardless of the presence of `service_worker`.
- Safari:
  - supports `background.scripts` (or `background.page`) and `background.service_worker`. If both are specified, uses `background.scripts` (or `background.page`), unless `preferred_environment` is set to `service_worker`.

To illustrate, this is an example of a cross-browser extension that supports `scripts` and `service_worker`. The example has this manifest.json file:

```json
{
  "name": "Demo of service worker + event page",
  "version": "1",
  "manifest_version": 3,
  "background": {
    "scripts": ["background.js"],
    "service_worker": "background.js"
  }
}
```

And, background.js contains:

```js
if (typeof browser === "undefined") {
  // Chrome does not support the browser namespace yet.
  globalThis.browser = chrome;
}
browser.runtime.onInstalled.addListener(() => {
  browser.tabs.create({ url: "http://example.com/first-run.html" });
});
```

When the extension is executed, this happens:

- in Chrome, the `service_worker` property is used, and a service worker starts that opens the tab because, in a Manifest V3 extension, Chrome only supports service workers for background scripts.
- in Firefox, the `scripts` property is used, and a script starts that opens the tab because Firefox only supports scripts for background scripts.
- in Safari, the `service_worker` property is used, and a service worker starts that opens the tab because Safari gives priority to using service workers for background scripts.

## Examples

```json
  "background": {
    "scripts": ["jquery.js", "my-background.js"]
  }
```

Load two background scripts.

```json
  "background": {
    "page": "my-background.html"
  }
```

Load a custom background page.

## Browser compatibility

{{Compat}}
