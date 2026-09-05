---
# Copy this file, rename it, fill it in. The filename becomes the item's slug.
# Only `name` and `category` are required — everything else is optional and
# simply doesn't render if you leave it out.

name: Example Transmitter 500
manufacturer: Example Manufacturing
category: wireless-video          # must match a slug in _data/categories.yml
summary: >-
  One or two sentences on what it is and when you'd reach for it. Written for a
  producer, not an engineer — the specs below carry the detail.

specs:
  Frequency: 2.0 – 2.7 GHz
  Output power: 100 mW – 1 W
  Latency: < 40 ms
  Inputs: 3G-SDI, HDMI
  Power: 12 V DC / V-lock

image: example.jpg                # file in assets/images/equipment/ (optional)
datasheet: example-tx500.pdf      # file in assets/datasheets/ (optional)
link: https://example.com/tx500   # manufacturer page (optional)

draft: true                       # remove this line to publish the item
---
