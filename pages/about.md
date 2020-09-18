---
layout: page
title: Conóceme
permalink: /conoceme/
weight: 3
---

# **Un pocoSobre Mi**


Hola! Soy **{{ site.author.name }}** :wave:,
Soy Multipotencial </br>
y me considero un curioso, autodidacta altamente creativo, con una gran capacidad de adaptación en entornos de constantes cambios, retos y desafíos a nivel personal y profesional.

<div class="row">
{% include about/skills.html title="Habilidades de Programacion" source=site.data.programming-skills %}

{% include about/skills.html title="Habilidades de Diseño" source=site.data.designer-skills %}


{% include about/skills.html title="Otras Habilidades" source=site.data.other-skills %}


{% include about/skills.html title="Idiomas" source=site.data.idiomas-skills %}
</div>

<div class="row">
{% include about/timeline.html %}
</div>
