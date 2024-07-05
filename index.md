---
layout: home
---

<div class="latest-div">
	{% assign latest = site.illusts | last %}

	<a href="{{ latest.url }}">
		<h2 class="post-title">{{ latest.title | escape }}</h2>
		<p class="post-meta">
			<time datetime="{{ latest.date | date_to_xmlschema }}">
				{{ latest.date | date: site.date_format }}
			</time>
		</p>

		{% include img_art.html page=latest %}

		<p>-</p>
	</a>

	<div class="latest-content">{{ latest.content }}</div>
</div>

<div class="recent-div">
	<h2 class="col-label">recent</h2>

	{% assign recents = site.documents %}
	{% assign recents = recents | sort: "date" | reverse %}

	{% assign idx = 0 %}

	<ul class="docs-ul">
		{% for i in (0..1) %}
			{% assign recent = recents[idx] %}
			{% if recent.url == latest.url %}
				{% assign idx = idx | plus: 1 %}
				{% assign recent = recents[idx] %}
			{% endif %}
			
			<li class="doc-link-li">
				<a class="post-link" href="{{ recent.url | relative_url }}">
					<span class="post-meta">{{ recent.collection }}</span>
					<h3 style="display:inline">{{ recent.title | escape }}</h3>
					<span class="post-meta">{{ recent.date | date: site.date_format }}</span>
				</a>
			</li>

			{% assign idx = idx | plus: 1 %}
		{% endfor %}
	</ul>
</div>

<style>
	.post-title, .post-meta {
		margin-top: 0.25em;
		margin-bottom: 0.25em;

		display: inline;
	}

	.latest-div img {
		width: 100%;
		max-height: 50vh;
		object-fit: contain;
	}

	.latest-div a {
		text-decoration: none;
	}

	.latest-content a {
		text-decoration: underline;
	}
</style>