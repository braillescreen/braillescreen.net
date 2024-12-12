---
layout: default.liquid
title: Blog
description: Rambling from a server administrator.
permalink: /blog
pagination:
  include: All
  per_page: 5
  permalink_suffix: "./{{num}}/"
  order: Desc
  sort_by: ["published_date"]
---
# {{ page.title }}
{{ page.description }}

[RSS](/blog.xml)

## posts
{% for post in paginator.pages %}
{% assign posttitle = post.title %}
{% if post.description and post.description != "" %}
{% assign posttitle = posttitle | append: " (" | append: post.description | append: ")" %}
{% endif %}
### [{{posttitle}}](/{{post.permalink}})
Published on <script>document.write(local_datetime_string("{{ post.published_date}}"));</script>

{{post.excerpt | strip_html}}

{%endfor%}

{%if paginator.previous_index or paginator.next_index%}
<nav aria-label="Pagination">

## Pagination
{{paginator.index}} / {{paginator.total_indexes}}

{%if paginator.previous_index%}
[Previous page](/{{paginator.previous_index_permalink}})
{%endif%}

{%if paginator.next_index%}
[Next page](/{{paginator.next_index_permalink}})
{%endif%}

{%if paginator.previous_index%}
[First page](/{{paginator.first_index_permalink}})
{%endif%}

{%if paginator.next_index%}
[Last page](/{{paginator.last_index_permalink}})
{%endif%}

</nav>
{%endif%}