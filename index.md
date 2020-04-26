---
layout: default
---

## HokStack - Stable HELM Chart Repository

{{ site.description }}

You can add this repository to your local helm configuration as follows :

```console
$ helm repo add {{ site.repo_name }} {{ site.url }}
$ helm repo update
$ helm search hok
```

## Charts

{% for helm_chart in site.data.index.entries %}
{% assign title = helm_chart[0] | capitalize %}
{% assign all_charts = helm_chart[1] | sort: 'created' | reverse %}
{% assign latest_chart = all_charts[0] %}

<h3>
  {% if latest_chart.icon %}
  <img src="{{ latest_chart.icon }}" style="height:1.2em;vertical-align: text-top;" />
  {% endif %}
  {{ title }}
</h3>

[Home]({{ latest_chart.home }}) \| [Source]({{ latest_chart.sources[0] }})

{{ latest_chart.description }}

```console
$ helm install {{ site.repo_name }}/{{ latest_chart.name }} --name myrelease --version {{ latest_chart.version }}
```

## Rollout for first team with default values

You can then check for the latest version by searching your Helm repositories for the HokStack

```
$ helm install hok/hokstack --name hok-team1 --set teamname=team1 --namespace team1
```

## Rollout for second team with default values

You can then check for the latest version by searching your Helm repositories for the HokStack

```
$ helm install hok/hokstack --name hok-team2 --set teamname=team2 --set metacontroller.crds.create=false --namespace team2
```

## Remove hadoop-on-kubernetes

Remove OneAgent custom resources and clean-up all remaining OneAgent Operator specific objects:

```
$ helm remove <release name> -n <namespace>
```

| Chart Version | App Version | Date |
|---------------|-------------|------|
{% for chart in all_charts -%}
{% unless chart.version contains "-" -%}
| [{{ chart.name }}-{{ chart.version }}]({{ chart.urls[0] }}) | {{ chart.appVersion }} | {{ chart.created | date_to_rfc822 }} |
{% endunless -%}
{% endfor -%}

{% endfor %}
