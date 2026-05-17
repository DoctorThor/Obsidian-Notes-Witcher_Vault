```base
properties:
  note.name:
    displayName: "Player:"
views:
  - type: cards
    name: Card View
    filters:
      and:
        - type == "pc"
        - file.folder != "z_Templates"
    order:
      - file.name
      - player
      - ac
      - hp
      - modifier
    image: note.image
    imageFit: contain
    cardSize: 230
    imageAspectRatio: 1

```
```base
views:
  - type: table
    name: Recently Modified
    sort:
      - property: file.mtime
        direction: DESC
```