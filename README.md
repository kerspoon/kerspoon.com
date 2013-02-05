
useful sites:

- https://github.com/Bilalh/bilalh.github.com/blob/source/_layouts/default.html
- http://unsemantic.com/css-documentation


        <a href="{{ post.url }}">
          {% if post.image %}
          <img src="{% post.image %}" width="242" height="100" alt="">
          {% else %}
          <img src="http://placehold.it/242x100" width="242" height="100" alt="">
          {% endif %}
        </a>