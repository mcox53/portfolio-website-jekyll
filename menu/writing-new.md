---
layout: page
title: Test
---
<section class="post-list">
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
			<span class = "post-meta date-label">{{ post.date | date: "%b %d" }}</span>
			<div class = "article-title">
				<a href="{{ site.github.url }}{{ post.url }}">{{ post.title }}</a>
			</div>
		</article>
	
		{% endfor %}
	</div>
</section>
