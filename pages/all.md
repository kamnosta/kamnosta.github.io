---
layout: home
title: all - kamnosta.net
permalink: /all

target_collections: []
---

<a href="/hidden/">
	<img src="/imgs_sketches/240608_heart_and_spiders_s02.png" alt="/imgs_sketches/240608_heart_and_spiders_s02.png" class="img-rendering-auto" id="all-index-img">
</a>

## /all

<div id="all-div">
	{% assign recents = site.documents %}
	{% assign recents = recents | sort: "date" %}

	{% assign idx = 0 %}

	<ul class="docs-ul">
		{% for recent in recents %}
			<li class="doc-link-li">
				<a class="post-link" href="{{ recent.url | relative_url }}">
					<h3 style="display:inline">{{ recent.title | escape }}</h3>
					<span class="post-meta">{{ recent.collection }}</span>
					<span class="post-meta">{{ recent.date | date: site.date_format }}</span>
				</a>
			</li>

			{% assign idx = idx | plus: 1 %}
		{% endfor %}
	</ul>
</div>

<style>
	#all-index-img {
		/*max-height: 24em;*/
		object-fit: contain;
	}
</style>