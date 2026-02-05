---
# Leave the homepage title empty to use the site title
title: ''
date: 2025-12-01
type: landing

sections:
  - block: resume-biography-classic
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: me
      text: ''
      button:
        text: Télécharger mon CV
        url: uploads/resume.pdf
    design:
      avatar:
        size: medium # Options: small (150px), medium (200px), large (250px)
        shape: circle # Options: circle (default), square, rounded
  - block: collection
    id: projects
    content:
      title: Projets
      filters:
        folders:
          - project
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
      title: Publications récentes
      count: 10
      text: ''
      filters:
        folders:
          - publications
    design:
      view: citation
#  - block: collection
#    id: blog
#    content:
#      title: Articles de blog récents
#      page_type: blog
#      count: 10
#      order: desc
#    design:
#      view: card
#      spacing:
#        padding: [0, 0, 0, 0]

---
