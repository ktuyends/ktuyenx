---
title: 'Hugo Apero Post using Quarto'
layout: single-sidebar
date: '2022-07-24'
publishDate: '2022-07-24'
lastUpdated: '2022-07-24'
slug: test-quarto
categories:
  - Sample
tags:
  - Sample
subtitle: 'Kiểm tra một số cú pháp khi viết bài trong blog sử dụng Quarto.'
summary: 'Kiểm tra một số cú pháp khi viết bài trong blog sử dụng Quarto.'
featured: yes
format: hugo
---



## 1. Một số cú pháp markdown cơ bản

### 1.1. Math

Example from the [mathjax demo](https://www.mathjax.org/#demo):

When `\(a \ne 0\)`, there are two solutions to \\(ax^2 + bx + c = 0\\) and they are

$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$

If I have a random \$ and another \$ in my text.

$$sd = \sqrt{\frac{\sum_{i=0}^{n}{(x_i-\bar x)^2}}{(n-1)} }$$

### 1.2. Heading

``` markdown
## h2 Heading {#custom-id}
### h3 Heading
#### h4 Heading
##### h5 Heading
###### h6 Heading
```

### 1.3. Comments

<!--
This is a comment
-->

### 1.4. Format:

*rendered as italicized text* **rendered as bold text** ***bold and italics*** ~~Strike through this text.~~

### 1.5. Blockquotes

> Đây là một đoạn code
>
> > Đây là một đoạn code trong một đoạn code

### 1.6. List

Dạng 1:

1.  Lorem ipsum dolor sit amet
2.  Consectetur adipiscing elit
3.  Integer molestie lorem at massa

Dạng 2:

-   Facilisis in pretium nisl aliquet
-   Nulla volutpat aliquam velit
    -   Phasellus iaculis neque
    -   Purus sodales ultricies

Dạng 3, Task list:

-   [x] Write the press release
-   [ ] Update the website
-   [ ] Contact the media

### 1.7. Code

**Inline:**

``` markdown
In this example, `<section></section>` should be wrapped as **code**.
```

<details>
<summary>
Hide Code
</summary>

Lạ nhỉ

``` python
import matplotlib.pyplot as plt
import numpy as np

t = np.arange(0.0, 2.0, 0.01)
s = 1 + np.sin(2*np.pi*t)
plt.plot(t, s)

plt.xlabel('time (s)')
plt.ylabel('voltage (mV)')
plt.title('About as simple as it gets, folks')
plt.grid(True)
plt.savefig("test.png")
plt.show()
```

Không hiểu thấu

</details>

**Gist:**

{{< gist spf13 7896402 >}}

### 1.11. Table

| Option | Description                                                               |
|--------|---------------------------------------------------------------------------|
| data   | path to data files to supply the data that will be passed into templates. |
| engine | engine to be used for processing templates. Handlebars is the default.    |
| ext    | extension to be used for dest files.                                      |

### 1.8. Link

<https://assemble.io>

<contact@revolunet.com>

[Assemble](https://assemble.io)

[Upstage](https://github.com/upstage/ "Visit Upstage!")

### 1.9. Footnotes

This is a digital footnote[^1]. This is a footnote with "label"[^2]

### 1.10. Image & Figure

![Minion](https://octodex.github.com/images/minion.png)

![Alt text](https://octodex.github.com/images/stormtroopocat.jpg "The Stormtroopocat")

### 1.11. Other Shorcodes

**Chèn Vimeo**

{{< vimeo 146022717 >}}

**Chèn Youtube**

{{< youtube KRCTOOJ7JrM >}}

[^1]: This is a digital footnote

[^2]: This is a footnote with "label"
