Before

<pre>
    site: {{ site | jsonify | escape }}
    page: {{ page | jsonify | escape }}
    layout: {{ layout | jsonify | escape }}
    content: {{ content | jsonify | escape }}
    paginator: {{ paginator | jsonify | escape }}
</pre>

{% for post in site.posts %}
  <article>
    <h2><a href="{{ post.url | prepend: site.baseurl }}" title="{{ post.title }}">{{ post.title }}</a></h2>
    <p>{{ post.excerpt }}</p>
  </article>
{% endfor %}

After
