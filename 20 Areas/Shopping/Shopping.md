---
id: Shopping
aliases:
  - Buy
tags:
---

- For anything I need to push up to the todoist shopping list, send it via the plugin

# [[Super Market]]

- the shopping list with [[Lil]] is on [this todoist list](https://app.todoist.com/app/project/shopping-list-6CrfFHqH5PM222Vr)

# [[Asian Groceries]]

# Indian supermarkets

- [ ] paneer
- [x] tamarind
- [ ] peanut
- [ ] almond
- [ ] papadom
- [ ] Chick Peas
- [ ] Nigella seeds

# Bulk Foods Shops

- [x] onion powder
- [x] garlic powder
- [x] black beans
- [ ] Epsom salt
- [ ] refill dish liquid
- [ ] peanut

# Garden Centre

    - [ ] Succulents
    - [ ] Mulch

- Stationary collapsed:: true

  - [ ] Staples
  - [x] Hot Glue Sticks
  - [x] Buy pavement chalk

  - [x] Pinter Paper collapsed:: true

- Chemist collapsed:: true

  - [x] Magnesium
  - [x] Multi-vit
  - [x] Ashwaganda collapsed:: true

- [[Hardware Shop]] collapsed:: true

  - Homeware shops collapsed:: true Kmart, Warehouse, Briscoes, Farmers
  - [x] Scooter handle for Dylan
  - [x] Bike handle for me
  - [ ] bike lock for dylan and Lil

- Jaycar collapsed:: true
  - [x] Calipers
  - CANCELED Writable CD (to back up ma's qigong)
  - [ ] More Rechargeable AAA battery
  - [x] Antaena for computer collapsed:: true

# [[Hardware Shop]]

# Tech Shop
- [ ] when on a good special, the [ninja multicooker](https://www.pbtech.co.nz/product/HOMNJA0015/Ninja-Foodi-OL650-14-in-One-SmartLid-Multi-Cooker)
# Clothes

- [ ] good underware for [[Lil]]
  - [ ] Djembe
  - [ ] 2x Dynamic Mic collapsed:: true
  - [x] got one,
  - [ ] Get another One
- [ ] Good Scissors

```dataview
LIST item.text
from #buy
FLATTEN file.lists as item
WHERE !item.task
WHERE contains(item.tags, "#buy")
SORT file.name DESC
```
