# Walmart picture inventory

Product photos for the Meal Planner shopping list pages, saved as `<item number>.jpg`. The item number
is the digits in the walmart.com link (for example `https://www.walmart.com/ip/44390948` is `44390948.jpg`).
Photos are JPEG, at most 400 x 400 px on a white background, quality 80 (about 5 to 27 KB each).

## catalog.json

`catalog.json` lists every saved photo: `id` (item number), `name` (product name), `source_url`
(the Walmart CDN image it came from), `saved` (date), plus `file`, `width`, `height` and `bytes`.
Check it before fetching a picture for a new list so nothing gets downloaded twice.

## How pages use it

Shopping pages built by `shopping_page.py` put a photo on every line whose item number is in the
catalog. For any other line they still try `../images/walmart/<item number>.jpg`, so a photo added
here later shows up without rebuilding the page. If there is no photo, the line shows a placeholder
with the item link.

## Adding photos

`picture_library.py missing <list spec>.json` lists items without a photo. `picture_library.py add
<urls.txt> --names <list spec>.json --push` takes lines of `<item number> <image URL>`, skips numbers
already in the catalog, resizes and saves the photos, updates the catalog, and pushes them all in one commit.
Image URLs come from the product pages (i5.walmartimages.com). Walmart blocks automated scraping of its
product pages, so the URLs are gathered separately.
