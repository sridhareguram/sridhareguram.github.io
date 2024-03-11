---
layout: page
title: Projects
permalink: /projects/
description: A growing collection of my cool projects.
nav: true
nav_order: 3
display_categories: [work-1, work-2]
horizontal: false
---

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{{ page.title }}</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
    }

    .projects {
      max-width: 800px;
      margin: 0 auto;
      padding: 20px;
    }

    .category {
      font-size: 24px;
      color: #333;
      margin-bottom: 10px;
    }

    .container {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
    }

    .project-card {
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      margin-bottom: 20px;
      width: 45%;
    }

    .project-card h3 {
      font-size: 20px;
      color: #0066cc;
      margin-bottom: 10px;
    }

    .project-card p {
      color: #666;
      line-height: 1.5;
    }
  </style>
</head>
<body>

<div class="projects">
  {% if site.enable_project_categories and page.display_categories %}
    {% for category in page.display_categories %}
      <h2 class="category">{{ category }}</h2>
      {% assign categorized_projects = site.projects | where: "category", category %}
      {% assign sorted_projects = categorized_projects | sort: "importance" %}
      <div class="container">
        {% for project in sorted_projects %}
          {% include projects.html %}
        {% endfor %}
      </div>
    {% endfor %}
  {% else %}
    {% assign sorted_projects = site.projects | sort: "importance" %}
    <div class="container">
      {% for project in sorted_projects %}
        {% include projects.html %}
      {% endfor %}
    </div>
  {% endif %}
</div>

</body>
</html>
