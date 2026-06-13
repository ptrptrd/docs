## Base

```base
views:
  - type: table
    name: Recent Journal Entries
    filters:
      and:
        - or:
            - file.inFolder("test/journal")
            - file.inFolder("test/sessions")
        - file.hasLink("test/Base")
    order:
      - file.name
      - title
    sort:
      - property: file.ctime
        direction: DESC

```