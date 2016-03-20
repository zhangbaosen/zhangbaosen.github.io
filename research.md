---
layout: default
title: Research
---

## Preprints

{% bibliography --query @article[arxiv=yes] %}

## Journal articles

{% bibliography --query @article[arxiv!=yes] %}

## Conference Proceedings

{% bibliography --query @inproceedings %}

## Thesis

{% bibliography --query @phdthesis %}