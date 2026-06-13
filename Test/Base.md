## Base

```base
views:
  - type: table
    name: Recent Journal Entries
    filters:
      and:
        - or:
            - file.inFolder("Test/Journal")
            - file.inFolder("Test/Sessions")
        - file.hasLink(this.file)
    order:
      - file.name
      - title
    sort:
      - property: file.ctime
        direction: DESC
    properties:
      file.name:
        displayName: Note
      file.ctime:
        displayName: Created
        format: yyyy-MM-dd

```