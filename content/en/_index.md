---
# Leave the homepage title empty to use the site title
title: ''
date: 2025-12-01
type: landing

design:
  spacing: '6rem'

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ''
      button:
        text: Download CV
        url: uploads/resume.pdf
      headings:
        about: ''
        education: ''
        interests: ''
    design:
      background:
        gradient_mesh:
          enable: true
      avatar:
        size: medium # Options: small (150px), medium (200px, default), large (320px), xl (400px), xxl (500px)
        shape: circle # Options: circle (default), square, rounded
  - block: collection
    id: projects
    content:
      title: Projects
      filters:
        folders:
          - projects
    design:
      # view: showcase
      # flip_alt_rows: true
      # columns: '1'
      view: article-grid
      fill_image: false
      columns: 3
      show_date: false
      show_read_time: false
      show_read_more: false
  - block: collection
    id: publications
    content:
      title: Recent Publications
      count: 10
      text: ''
      filters:
        folders:
          - publications
    design:
      view: citation
  - block: collection
    id: blog
    content:
      title: Recent Blog Posts
      page_type: blog
      count: 10
      order: desc
    design:
      view: card
      spacing:
        padding: [0, 0, 0, 0]

---
