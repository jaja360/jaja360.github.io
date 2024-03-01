---
title: ''
date: 2024-02-28
type: landing

sections:
  - block: about.biography
    id: about
    content:
      title: Biography
      username: admin

  - block: portfolio
    id: projects
    design:
      columns: '1'
      view: showcase
      flip_alt_rows: false
    content:
      title: Projects
      filters:
        folders:
          - project

  - block: collection
    id: publications
    design:
      columns: '2'
      view: citation
    content:
      title: Recent Publications
      filters:
        folders:
          - publication
        exclude_featured: true

  - block: contact
    id: contact
    design:
      columns: '2'
    content:
      title: Contact
      email: champagne_gareau.jael@uqam.ca
      phone: (514) 826-3867
      # appointment_url: 'https://calendly.com'
      address:
        street: 201, Avenue du Président-Kennedy, PK-4285
        city: Montréal
        region: QC
        postcode: 'H2X 3Y7'
        country: Canada
        country_code: CA
      # directions:
      # office_hours:
      #  - 'Monday 10:00 to 13:00'
      coordinates:
        latitude: '45.509249'
        longitude: '-73.568511'
      contact_links:
        - icon: twitter
          icon_pack: fab
          name: DM Me
          link: 'https://twitter.com/jaja360'
      autolink: true
      form:
        provider: formspree
        formspree:
          id: mbjnypoa

---
