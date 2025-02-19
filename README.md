# jekyll-strapi-mod

>This plugin is a fork of the original jekyll-strapi plugin. The jekyll-strapi-mod plugin is compatible with Strapi v4

## Install

Add the "jekyll-strapi-mod" gem to your Gemfile:

```ruby
gem "jekyll-strapi-mod"
```

Then add "jekyll-strapi-mod" to your plugins in `_config.yml`:

```yaml
plugins:
    - jekyll-strapi-mod
```

## Configuration

```yaml
strapi:
    # Your API endpoint (optional, default to http://localhost:1337/api)
    endpoint: http://localhost:1337/api
    # Your REST API endpoint query string to specify a parameter for example http://localhost:1337/api/posts?populate=%2A (optional, default to populate=*)
    parameter: populate=*
    # Collections, key is used to access in the strapi.collections
    # template variable
    collections:
        # Example for an "articles" collection
        articles:         
            # Collection name (optional)
            type: article
            # Permalink used to generate the output files (eg. /articles/:id).
            permalink: /articles/:id/
            # Layout file for this collection
            layout: strapi_article.html
            # Generate output files or not (default: false)
            output: true
```

## Usage

This plugin provides the `strapi` template variable. This template provides access to the collections defined in the configuration.

### Using Collections

Collections are accessed by their name in `strapi.collections`. The `articles` collections is available at `strapi.collections.articles`.

To list all documents of the collection:

```html
{% for post in strapi.collections.articles %}
<article>
    <header>
        {{ post.attributes.title }}
    </header>
    <div class="body">
        {{ post.attributes.content }}
    </div>
</article>
{% endfor %}
```
