# Walmart picture inventory

Save product photos here as `<item number>.jpg`, where the item number is the digits in the
walmart.com link (for example `https://www.walmart.com/ip/44390948` is `44390948.jpg`).

Shopping list pages built by `shopping_page.py` look for `../images/walmart/<item number>.jpg`
on every line. When the file exists the picture shows; otherwise the line shows a placeholder
with the item link. No page rebuild is needed after adding a photo.

Tip: keep photos small (about 300 px wide, under 40 KB) so the list loads fast on a phone.
