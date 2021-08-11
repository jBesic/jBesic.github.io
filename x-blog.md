{% for post in site.posts %}
  <article>
    <h2><a href="{{ post.url | prepend: site.baseurl }}" title="{{ post.title }}">{{ post.title }}</a></h2>
    <p>{{ post.summary }}</p>
  </article>
{% endfor %}
