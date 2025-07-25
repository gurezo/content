---
title: "<li>: The List Item element"
slug: Web/HTML/Reference/Elements/li
page-type: html-element
browser-compat: html.elements.li
sidebar: htmlsidebar
---

The **`<li>`** [HTML](/en-US/docs/Web/HTML) element is used to represent an item in a list. It must be contained in a parent element: an ordered list ({{HTMLElement("ol")}}), an unordered list ({{HTMLElement("ul")}}), or a menu ({{HTMLElement("menu")}}). In menus and unordered lists, list items are usually displayed using bullet points. In ordered lists, they are usually displayed with an ascending counter on the left, such as a number or letter.

{{InteractiveExample("HTML Demo: &lt;li&gt;", "tabbed-shorter")}}

```html interactive-example
<p>Apollo astronauts:</p>

<ul>
  <li>Neil Armstrong</li>
  <li>Alan Bean</li>
  <li>Peter Conrad</li>
  <li>Edgar Mitchell</li>
  <li>Alan Shepard</li>
</ul>
```

```css interactive-example
p,
li {
  font:
    1rem "Fira Sans",
    sans-serif;
}

p {
  font-weight: bold;
}
```

## Attributes

This element includes the [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).

- `value`
  - : This integer attribute indicates the current ordinal value of the list item as defined by the {{HTMLElement("ol")}} element. The only allowed value for this attribute is a number, even if the list is displayed with Roman numerals or letters. List items that follow this one continue numbering from the value set. This attribute has no meaning for unordered lists ({{HTMLElement("ul")}}) or for menus ({{HTMLElement("menu")}}).
- `type` {{Deprecated_inline}}
  - : This character attribute indicates the numbering type:
    - `a`: lowercase letters
    - `A`: uppercase letters
    - `i`: lowercase Roman numerals
    - `I`: uppercase Roman numerals
    - `1`: numbers

    This type overrides the one used by its parent {{HTMLElement("ol")}} element, if any.

    > [!NOTE]
    > This attribute has been deprecated; use the CSS {{cssxref("list-style-type")}} property instead.

## Examples

For more detailed examples, see the {{htmlelement("ol")}} and {{htmlelement("ul")}} pages.

### Ordered list

```html
<ol>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ol>
```

#### Result

{{EmbedLiveSample("Ordered_list")}}

### Ordered list with a custom value

```html
<ol type="I">
  <li value="3">third item</li>
  <li>fourth item</li>
  <li>fifth item</li>
</ol>
```

#### Result

{{EmbedLiveSample("Ordered_list_with_a_custom_value")}}

### Unordered list

```html
<ul>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ul>
```

#### Result

{{EmbedLiveSample("Unordered_list")}}

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
        The end tag can be omitted if the list item is immediately followed by
        another <code>&lt;li&gt;</code> element, or if there is no more
        content in its parent element.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        An {{HTMLElement("ul")}}, {{HTMLElement("ol")}}, or
        {{HTMLElement("menu")}} element. Though not a conforming usage,
        the obsolete {{HTMLElement("dir")}} can also be a parent.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role"
            >listitem</a
          ></code
        >
        when child of an
        <code><a href="/en-US/docs/Web/HTML/Reference/Elements/ol">ol</a></code
        >, <code><a href="/en-US/docs/Web/HTML/Reference/Elements/ul">ul</a></code> or
        <code><a href="/en-US/docs/Web/HTML/Reference/Elements/menu">menu</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role"><code>menuitem</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role"><code>menuitemcheckbox</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role"><code>menuitemradio</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role"><code>option</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role"><code>radio</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role"><code>separator</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role"><code>tab</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role"><code>treeitem</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>{{domxref("HTMLLIElement")}}</td>
    </tr>
  </tbody>
</table>

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- Other list-related HTML Elements: {{HTMLElement("ul")}}, {{HTMLElement("ol")}}, {{HTMLElement("menu")}}, and the obsolete {{HTMLElement("dir")}};
- CSS properties that may be specially useful to style the `<li>` element:
  - the {{cssxref("list-style")}} property, to choose the way the ordinal is displayed,
  - [CSS counters](/en-US/docs/Web/CSS/CSS_counter_styles/Using_CSS_counters), to handle complex nested lists,
  - the {{cssxref("margin")}} property, to control the indent of the list item.
