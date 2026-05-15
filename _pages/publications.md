---
title: "GrunnSec Research Group - Publications"
layout: gridlay
excerpt: "GrunnSec Research Group -- Publications."
sitemap: false
permalink: /publications/
---


<h1 class="sapienza-text"> Publications</h1>


<script type="text/javascript">
    <!--
    // Toggle Display of BibTeX
    function toggleBibtex(articleid) {
        var bib = document.getElementById('bib_'+articleid);
        if (bib) {
            if(bib.className.indexOf('bibtex') != -1) {
                bib.className.indexOf('noshow') == -1?bib.className = 'bibtex noshow':bib.className = 'bibtex';
            }
        } else {
            return;
        }
    }
-->
    </script>
(For a full list see [below](#list))

{% assign number_printed = 0 %}
{% for publi in site.data.publist %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if publi.highlight == 1 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
 <div class="well">
  <pubtit>{{ publi.title }}</pubtit>
  <img src="{{ site.url }}{{ site.baseurl }}/images/paperpic/{{ publi.image }}" class="img-responsive" width="33%" style="float: left" />
  <p>{{ publi.description }}</p>
  <p><em>{{ publi.authors }}</em></p>
  <p><strong><a href="{{ publi.link.url }}">{{ publi.link.display }}</a>&nbsp;&nbsp;
  <a href="{{ publi.code }}">Code</a>&nbsp;&nbsp;
   {% if publi.bibtex %}<a href="javascript:toggleBibtex('{{ publi.title }}')">BibTeX</a>{% endif %}&nbsp;&nbsp;
   {% if publi.blog %}<a href="{{ site.url }}{{ site.baseurl }}/{{ publi.blog }}">Blog Post</a>{% endif %}
  </strong></p>
<div id="bib_{{ publi.title }}" class="bibtex noshow">
<pre>
{{publi.bibtex}}
</pre>
</div>
  <p class="text-danger"><strong> {{ publi.news1 }}</strong></p>
  <p> {{ publi.news2 }}</p>
 </div>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endif %}
{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}


<p> &nbsp; </p>

<a name="list"></a>
<h3 class="sapienza-text">Full List</h3>

<div class="publications-list">
{% assign prev_year = 1900 %}
{% for publi in site.data.publist %}

{% if publi.year != prev_year %}
<div class="year-section">
  <h4 class="pub-year">{{ publi.year }}</h4>
  {% assign prev_year = publi.year %}
</div>
{% endif %}

<div class="publication-entry">
  <p>
    <span class="authors">{{ publi.authors }}</span>.
    "<span class="paper-title">{{ publi.title }}</span>".
    <span class="venue">{{ publi.publisher }}</span>, {{ publi.year }}.
    {% if publi.link.url %}<a href="{{ publi.link.url }}">[PDF]</a>{% endif %}
    {% if publi.code %}<a href="{{ publi.code }}">[Code]</a>{% endif %}
    {% if publi.bibtex %}<a href="javascript:toggleBibtex('{{ publi.title }}list')">[BibTeX]</a>{% endif %}
    {% if publi.blog %}<a href="{{ site.url }}{{ site.baseurl }}/{{ publi.blog }}">[Blog]</a>{% endif %}
  </p>
  {% if publi.bibtex %}
  <div id="bib_{{ publi.title }}list" class="bibtex noshow">
    <pre>{{ publi.bibtex }}</pre>
  </div>
  {% endif %}
</div>
{% endfor %}
</div>
