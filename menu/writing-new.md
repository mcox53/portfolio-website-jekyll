---
layout: page
title: Test
---
<section class="posts">
	<div class = "container">
		{% for post in site.posts %}
		{% unless post.next %}
			<h3>{{ post.date | date: '%Y' }}</h3>
		{% else %}
			{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
			{% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
			{% if year != nyear %}
				<h3>{{ post.date | date: '%Y' }}</h3>
			{% endif %}
		{% endunless %}
	
		
		<article class="post-item">
			<span class = "post-meta date-label">{{ post.data | date: "%b %d" }}</span>
			<div class = "article-title"><a class="post-link" href={{ post.url | prepend: site.baseurl | prepend: site.url }}">{{ post.title }}
		</article>
	
	{% endfor %}
</ul>
