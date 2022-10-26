---
layout: page
title: Conóceme
permalink: /conoceme/
weight: 3
---

# **Un pocoSobre Mi**


Hola! Me llamo **{{ site.author.name }}** :wave: y soy Ing. de Sistemas con más de 13 años de experiencia en la industria del desarrollo de software y calidad. </br> En lo personal soy Multipotencial y me considero un curioso, autodidacta altamente creativo, mi pasión es la fotografía, videografía, comunicación, música (Tocar la guitarra), café, libros, pasear por la naturaleza, viajar, conversaciones profunda

<div class="row">
  {% include about/skills.html title="Habilidades de Programacion" source=site.data.programming-skills %}
  {% include about/skills.html title="Habilidades de Diseño" source=site.data.designer-skills %}
</div>

<div class="row">
  {% include about/skills.html title="Otras Habilidades" source=site.data.other-skills %}
  {% include about/skills.html title="Idiomas" source=site.data.idiomas-skills %}
</div>

<div class="row">
  {% include about/timeline.html %}
</div>
