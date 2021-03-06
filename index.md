---
layout: default
title: Home
---

{% assign numgrant = 0 %}
{% for grant in site.grants %}
  {% assign numgrant = numgrant | plus: 1 %}
{% endfor %}

An increasing number of researchers are sharing their grant proposals
openly. They do this to open up science so that all stages of the process can
benefit from better interaction and communication and to provide examples for
early career scientists writing grants. This is a list of {{ numgrant }} of
these proposals to help you find them.

<table>
  <tr>
	<th>Year</th>
	<th>Funder</th>
	<th>Title</th>
	<th>Funded</th>
  </tr>
{% for grant in site.grants %}
  <tr>
    <td>{{ grant.year }}</td>
	<td>{{ grant.funder }}</td>
	<td><a href="{{ grant.link }}">{{ grant.title }}</a> <small> by {{ grant.author }}</small></td>
	{% if grant.status == 'funded' %}
	  <td>Yes</td>
	{% elsif grant.status == 'unfunded' %}
	  <td>No</td>
	{% else %}
	  <td>?</td>
	{% endif %}
  </tr>
{% endfor %}
