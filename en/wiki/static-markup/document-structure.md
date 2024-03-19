---
title: "Page structure elements in {{ wiki-full-name }}"
description: "In this tutorial, you will learn about page structure elements in {{ wiki-name }}."
---

# Page structure

## Clusters and headings {#sections-and-titles}

Add headings to divide a page into clusters. To format the heading, insert one to six `#` symbols and a space before the heading text. The heading level changes based on how many `#` symbols you type.

You can use a different markup style for the first- and second-level headings:

* For the first-level heading, insert any number of `=` symbols in the line following the heading.

* For the second-level heading, insert any number of hyphens `-` in the line following the heading.

| Markup | Result |
--- | ---
| `# First-level header` | ![](../../_assets/wiki/h1.png) |
| `First-level header`<br>`======` | ![](../../_assets/wiki/h1.png) |
| `## Second-level header` | ![](../../_assets/wiki/h2.png) |
| `Second-level header`<br>`--------------` | ![](../../_assets/wiki/h2.png) |
| `### Third-level header` | ![](../../_assets/wiki/h3.png) |
| `#### Fourth-level header` | ![](../../_assets/wiki/h4.png) |
| `##### Fifth-level header` | ![](../../_assets/wiki/h5.png) |
| `###### Sixth-level header` | ![](../../_assets/wiki/h6.png) |

### Getting a link to a cluster {#section-link}

1. Hover over the cluster title and click **§** that appears to the right of the title.

1. Copy the cluster address from the browser's address bar.

For more information, see [{#T}](../actions/anchor.md).

## Paragraphs {#section_paragraphs}

To start a new paragraph, insert an empty line after the previous one:

```
First line of the paragraph.
Second line of the paragraph.

New paragraph.
```

{% cut "See the result" %}

![](../../_assets/wiki/new-par.png)

{% endcut %}

{% note info %}

To add multiple empty lines between text blocks, use a `\` backslash at the beginning of each empty line.

{% endnote %}

## Margins {#section_spacing}

- Indents created with spaces at the beginning of the line are used for formatting [lists](./lists.md) of the second and third levels.

- If you add spaces to the beginning of a paragraph, they will be ignored. The paragraph will be displayed without indentation.

- To indent a paragraph, insert a few non-breaking spaces using the code `&nbsp;`.


| Markup | Result |
--- | ---
| ![](../../_assets/wiki/spacing1.png) | ![](../../_assets/wiki/spacing2.png) |


## Horizontal line {#section_rulers}

- To insert a horizontal line between parts of the text, insert three or more hyphens `-`, <q>asterisks</q>`*`, underscores `_` in a row on an empty line.

- If you use hyphens, add an empty line before the line. Otherwise the previous line will turn into a heading.

| Markup | Result |
--- | ---
| `---` | ![](../../_assets/wiki/3-rules.png) |
| `****` | ![](../../_assets/wiki/3-rules.png) |
| `___` | ![](../../_assets/wiki/3-rules.png) |

## Collapsed text {#section-cut}

{% list tabs %}

- New editor

   1. In the line before the text, insert the `{% cut "` symbols followed by the `cut` title and the `" %}` symbols.

   1. From a new line, enter the text that will be hidden under the `cut` title.

   1. After the text, insert the `{% endcut %}` symbols.

   Markup:

   ```
   {% cut "Cut title" %}

   Content to display on click.

   {% endcut %}
   ```

   Result:

   {% cut "Cut title" %}

   Content to display on click.

   {% endcut %}

- Old editor

   To make part of the page's text collapsible:

   1. In the line before the text, insert the `<{` symbols and the `cut` title.

   1. From a new line, enter the text that will be hidden under the `cut` title.

   1. After the text, insert the `}>` symbols.

   | Markup | Result |
   --- | ---
   | `<{ Read the entire text`<br>`You can see this text`<br>`by clicking _Read the entire text_.`<br>`}>` | ![](../../_assets/wiki/cut.png) |

{% endlist %}
