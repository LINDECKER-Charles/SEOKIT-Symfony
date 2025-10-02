# Symfony SEO Kit

A simple and extensible kit to manage **SEO and social sharing** in your Symfony projects via Twig.
This package provides a common base for essential tags such as **`<title>`**, **meta description**, **Open Graph (Facebook, LinkedIn, etc.)**, **Twitter Cards**, **robots directives**, theme colors, and preview images. The goal is to unify SEO management in your views, reduce code duplication, and help improve both the visibility of your application in search engines and the appearance of your content when shared on social media.

---

## 🚀 Features

* Centralized SEO tags in a single template (`base.html.twig`).
* Secure default values (title, description, image) to avoid missing tags.
* Native support for:

  * **Classic HTML tags** (`title`, `meta description`).
  * **Open Graph** (`og:title`, `og:description`, `og:image`, `og:url`, `og:type`).
  * **Twitter Cards** (`twitter:title`, `twitter:description`, `twitter:image`, `twitter:card`).
  * **Robots directives** (`index/noindex`, `follow/nofollow`).
  * **Theme color** for modern browsers.
* Smart default image handling: each page can define its own or inherit a global one.
* Easy to extend Twig blocks for specific cases (blog posts, product pages, etc.).

---

## 📦 Installation

1. Copy the provided files into your Symfony project:

   * `base.html.twig` → holds the `<head>` structure.
   * `exemple.html.twig` → a concrete usage example.

2. Make sure your templates extend this file (`extends`).

3. Customize the default values in `base.html.twig` to match your project.

---

## 🛠 Usage

### 1. Extend the template

In your views, extend the `base.html.twig` template:

```twig
{% extends 'base.html.twig' %}
```

### 2. Define main tags

Set the key blocks for each page:

```twig
{% block title %}Homepage{% endblock %}
{% block meta_description %}Welcome to my SEO-optimized Symfony site{% endblock %}
{% block img %}/images/preview.png{% endblock %}
```

All other tags (Open Graph, Twitter Cards) will automatically use these values.

### 3. Customize if needed

You can override individual tags:

```twig
{% block og_type %}article{% endblock %}
{% block twitter_card %}summary{% endblock %}
{% block meta_robots %}noindex, nofollow{% endblock %}
```

You can also override `theme_color`, `og:url`, or define a custom Open Graph title if necessary.

---

## 📖 Full Example

```twig
{% extends 'base.html.twig' %}

{% block title %}{{ 'setup.title'|trans }}{% endblock %}
{% block meta_description %}{{ 'setup.meta'|trans }}{% endblock %}
{% block img %}/preview/setup.png{% endblock %}

{# Optional overrides #}
{% block og_type %}article{% endblock %}
{% block twitter_card %}summary_large_image{% endblock %}
```

---

## ✅ Best Practices

* Always define a unique `title` and `description` for each page.
* Provide a properly sized image (1200x630px recommended for Open Graph and Twitter). Too small or stretched images may not render correctly.
* Use `meta_robots` to control indexing of sensitive pages (e.g. login, back-office, private content).
* Test your pages with tools such as:

  * [Google Rich Results Test](https://search.google.com/test/rich-results).
  * [Facebook Open Graph Debugger](https://developers.facebook.com/tools/debug/).
  * [Twitter Card Validator](https://cards-dev.twitter.com/validator).
* Set up an XML sitemap and reference it in your project to help search engines crawl your site.
* Remember SEO also depends on text content quality, performance (Core Web Vitals), and overall HTML structure.

---

## 📜 License

Free to use, modify, and adapt in your Symfony projects. You can integrate it as-is or adjust it to fit your specific SEO needs.
