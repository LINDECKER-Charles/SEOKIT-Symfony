# KIT SEO pour Symfony

Un kit simple et extensible pour gérer le **SEO et le partage social** dans vos projets Symfony via Twig.
Ce package fournit une base commune pour les balises essentielles comme **`<title>`**, **meta description**, **Open Graph (Facebook, LinkedIn, etc.)**, **Twitter Cards**, directives **robots**, couleurs de thème, et images de prévisualisation. L’objectif est d’unifier la gestion SEO dans vos vues, réduire la duplication de code et vous aider à améliorer la visibilité de votre application dans les moteurs de recherche ainsi que l’apparence lors du partage sur les réseaux sociaux.

---

## 🚀 Fonctionnalités

* Centralisation des balises SEO dans un seul template (`base.html.twig`).
* Valeurs par défaut sécurisées (titre, description, image) pour éviter les oublis.
* Support natif pour :

  * **Balises HTML classiques** (`title`, `meta description`).
  * **Open Graph** (`og:title`, `og:description`, `og:image`, `og:url`, `og:type`).
  * **Twitter Cards** (`twitter:title`, `twitter:description`, `twitter:image`, `twitter:card`).
  * **Robots directives** (`index/noindex`, `follow/nofollow`).
  * **Theme color** pour navigateurs modernes.
* Gestion intelligente des images par défaut : chaque page peut définir la sienne ou hériter d’une image générique.
* Possibilité d’étendre facilement les blocs Twig pour des cas spécifiques (articles de blog, fiches produits, etc.).

---

## 📦 Installation

1. Copiez les fichiers fournis dans votre projet Symfony :

   * `base.html.twig` → contenu du `<head>` principal.
   * `exemple.html.twig` → exemple concret d’utilisation.

2. Assurez-vous que votre application inclut bien ce fichier dans toutes les pages (via `extends`).

3. Personnalisez les valeurs par défaut dans `base.html.twig` pour correspondre à votre projet.

---

## 🛠 Utilisation

### 1. Étendre le template

Dans vos vues, étendez simplement le `base.html.twig` :

```twig
{% extends 'base.html.twig' %}
```

### 2. Définir les balises principales

Déclarez les blocs clés pour chaque page :

```twig
{% block title %}Page d'accueil{% endblock %}
{% block meta_description %}Bienvenue sur mon site Symfony optimisé SEO{% endblock %}
{% block img %}/images/preview.png{% endblock %}
```

Toutes les autres balises (Open Graph, Twitter Cards) se rempliront automatiquement avec ces valeurs.

### 3. Personnaliser si nécessaire

Chaque balise peut être surchargée individuellement :

```twig
{% block og_type %}article{% endblock %}
{% block twitter_card %}summary{% endblock %}
{% block meta_robots %}noindex, nofollow{% endblock %}
```

Vous pouvez également modifier le `theme_color`, l’`og:url` ou définir un titre distinct pour Open Graph si besoin.

---

## 📖 Exemple complet

```twig
{% extends 'base.html.twig' %}

{% block title %}{{ 'setup.title'|trans }}{% endblock %}
{% block meta_description %}{{ 'setup.meta'|trans }}{% endblock %}
{% block img %}/preview/setup.png{% endblock %}

{# Surcharge facultative #}
{% block og_type %}article{% endblock %}
{% block twitter_card %}summary_large_image{% endblock %}
```

---

## ✅ Bonnes pratiques

* Toujours définir un `title` et une `description` unique par page.
* Fournir une image adaptée (1200x630px recommandé pour Open Graph et Twitter). Une image trop petite ou disproportionnée risque de ne pas s’afficher correctement.
* Utiliser `meta_robots` pour contrôler l’indexation des pages sensibles (ex. page de login, back-office, contenu privé).
* Vérifier le rendu de vos pages avec des outils comme :

  * [Rich Results Test](https://search.google.com/test/rich-results) de Google.
  * [Open Graph Debugger](https://developers.facebook.com/tools/debug/).
  * [Twitter Card Validator](https://cards-dev.twitter.com/validator).
* Mettre en place un sitemap XML et le référencer pour faciliter le crawl des moteurs de recherche.
* Garder à l’esprit que le SEO dépend aussi du contenu textuel, des performances (Core Web Vitals) et de la structure HTML.

---

## 📜 Licence

Libre d’utilisation, de modification et d’adaptation dans vos projets Symfony. Vous pouvez l’intégrer tel quel ou l’adapter pour coller à vos besoins spécifiques en SEO.
