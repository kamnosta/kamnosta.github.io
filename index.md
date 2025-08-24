---
layout: home
---

<div class="latest-div">
	
	{% assign latest = site.ishalvingover | last %}
	{% comment %}
	{% assign latest = site.heartstudies | where: "url", "/heartstudies/240802-the-lifting-of-the-head" | first %}
	{% endcomment %}

	<a href="{{ latest.url }}">
		<h1 class="post-title">{{ latest.title | escape }}</h1>
		<p class="post-meta">
			<time datetime="{{ latest.date | date_to_xmlschema }}">
				{{ latest.date | date: site.date_format }}
			</time>
		</p>

		{% comment %}
		{% include img_art.html page=latest render_auto=latest.render_auto %}
		{% endcomment %}
		<h2>{{ latest.firstverse }}</h2>
		{% assign imgname = latest.date | date: site.date_format_imgs | append: "_iho" | append: latest.slug | append: ".png" %}
		<img alt="{{ imgname }}" src="/imgs_ishalvingover/{{ imgname }}">
		
		<p>-</p>
	</a>

	<div class="latest-content iho_content_div">{{ latest.content }}</div>
</div>

<p>- -</p>

<div class="recent-div">
	{% assign recents = site.documents %}
	{% assign recents = recents | sort: "date" | reverse %}

	{% assign idx = 0 %}

	<ul class="docs-ul">
		{% for i in (0..0) %}
			{% assign recent = recents[idx] %}
			{% for inf in (0..999) %}
				{% if recent.collection != "posts" %}
					{% assign idx = idx | plus: 1 %}
					{% assign recent = recents[idx] %}
				{% else %}
					{% break %}
				{% endif %}
			{% endfor %}
			
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

	.iho_content_div {
		text-align: left;
		text-indent: 0.5em;
	}
</style>