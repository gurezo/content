---
title: "<dd>: The Description Details element"
slug: Web/HTML/Reference/Elements/dd
page-type: html-element
browser-compat: html.elements.dd
sidebar: htmlsidebar
---

The **`<dd>`** [HTML](/en-US/docs/Web/HTML) element provides the description, definition, or value for the preceding term ({{HTMLElement("dt")}}) in a description list ({{HTMLElement("dl")}}).

{{InteractiveExample("HTML Demo: &lt;dd&gt;", "tabbed-standard")}}

```html interactive-example
<p>Cryptids of Cornwall:</p>

<dl>
  <dt>Beast of Bodmin</dt>
  <dd>A large feline inhabiting Bodmin Moor.</dd>

  <dt>Morgawr</dt>
  <dd>A sea serpent.</dd>

  <dt>Owlman</dt>
  <dd>A giant owl-like creature.</dd>
</dl>
```

```css interactive-example
p,
dt {
  font-weight: bold;
}

dl,
dd {
  font-size: 0.9rem;
}

dd {
  margin-bottom: 1em;
}
```

## Attributes

This element only includes the [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).

## Examples

For examples, see the [examples provided for the `<dl>` element](/en-US/docs/Web/HTML/Reference/Elements/dl#examples).

## Technical summary

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>None.</td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>
        The start tag is required. The end tag may be omitted if this element is
        immediately followed by another <code>&#x3C;dd></code> element or a
        {{HTMLElement("dt")}} element, or if there is no more content in
        the parent element.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        A {{HTMLElement("dl")}} or a
        {{HTMLElement("div")}} that is a child of a
        {{HTMLElement("dl")}}.<br />This element can be used after a
        {{HTMLElement("dt")}} or another <code>&lt;dd&gt;</code>
        element.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role"
          >No corresponding role</a
        >
        </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>No <code>role</code> permitted</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>{{domxref("HTMLElement")}}</td>
    </tr>
  </tbody>
</table>

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{HTMLElement("dl")}}
- {{HTMLElement("dt")}}
