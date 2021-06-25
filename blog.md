### blog posts:
  {% for post in site.posts %}
  <article>
    <h2>
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </h2>
    <time datetime="{{ post.date | date: "%Y-%m-%d" }}">{{ post.date | date_to_long_string }}</time>
    {{ post.content }}
  </article>
{% endfor %}

For comments and feedback:
[Instagram](https://www.instagram.com/michele.libralato)

[Twitter](https://www.twitter.com/mi_libr)

[ResearchGate](https://www.researchgate.net/profile/Michele-Libralato)

[LinkedIn](https://www.linkedin.com/in/michele-libralato-1a9a07102/)

[GitHub](https://github.com/michele-libralato)
