# Extended Shortcode - typeit


The `typeit` shortcode provides typing animation based on [TypeIt](https://typeitjs.com/) library.

<!--more-->

Just insert your content in the `typeit` shortcode and that’s it.

## 1 Simple Content {#simple-content}

Simple content is allowed in `Markdown` format and **without** rich block content such as images and more...

Example `typeit` input:

```go-html-template
{{</* typeit */>}}
This is a *paragraph* with **typing animation** based on [TypeIt](https://typeitjs.com/)...
{{</* /typeit */>}}
```

The rendered output looks like this:

{{< typeit >}}
This is a *paragraph* with **typing animation** based on [TypeIt](https://typeitjs.com/)...
{{< /typeit >}}

Alternatively, you can use custom **HTML tags**.

Example `typeit` input with `h4` tag:

```go-html-template
{{</* typeit tag=h4 */>}}
This is a *paragraph* with **typing animation** based on [TypeIt](https://typeitjs.com/)...
{{</* /typeit */>}}
```

The rendered output looks like this:

{{< typeit tag=h4 >}}
This is a *paragraph* with **typing animation** based on [TypeIt](https://typeitjs.com/)...
{{< /typeit >}}

## 2 Code Content {#code-content}

Code content is allowed and will be highlighted by named parameter `code` for the type of code language.

Example `typeit` input with `code`:

```go-html-template
{{</* typeit code=java */>}}
public class HelloWorld {
    public static void main(String []args) {
        System.out.println("Hello World");
    }
}
{{</* /typeit */>}}
```

The rendered output looks like this:

{{< typeit code=java >}}
public class HelloWorld {
    public static void main(String []args) {
        System.out.println("Hello World");
    }
}
{{< /typeit >}}

## 3 Group Content {#group-content}

All typing animations start at the same time by default.
But sometimes you may want to start a set of `typeit` contents in order.

A set of `typeit` contents with the same value of named parameter `group` will start typing animation in sequence.

Example `typeit` input with `group`:

```go-html-template
{{</* typeit group=paragraph */>}}
**First** this paragraph begins
{{</* /typeit */>}}

{{</* typeit group=paragraph */>}}
**Then** this paragraph begins
{{</* /typeit */>}}
```

The rendered output looks like this:

{{< typeit group=paragraph >}}
**First** this paragraph begins
{{< /typeit >}}

{{< typeit group=paragraph >}}
**Then** this paragraph begins
{{< /typeit >}}

---

> Author: [Lruihao](https://lruihao.cn)  
> URL: https://fixit.lruihao.cn/extended-shortcode-typeit/  
