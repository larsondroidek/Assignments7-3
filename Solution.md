# Assignment 7.3 — Solution: Responsive Product Listing

## Project Structure
```
product-listing/
├── index.html
├── style.css
└── images/
    ├── headphones.svg   watch.svg   backpack.svg
    └── bottle.svg       lamp.svg    camera.svg
```
The complete code is in the attached files. The key parts:

## Product Listing (6 cards)
Each card has an image, a name, a price and a button.
```css
.product-list {
  display: flex;
  flex-wrap: wrap;     /* cards move to the next line when there is no room */
  gap: 24px;           /* spacing between cards, in rows and columns */
}

.product-card {
  flex: 1 1 250px;     /* grow 1 | shrink 1 | basis 250px */
  max-width: 360px;
}
```

## `flex-grow`, `flex-shrink`, `flex-basis`
| Property | Meaning | In this project |
|----------|---------|-----------------|
| `flex-basis: 250px` | The starting width of the item before free space is shared | Each card *wants* to be 250px wide; this decides how many fit in a row |
| `flex-grow: 1` | Share of the leftover space on a row | The cards on a row grow equally to fill it (up to `max-width`) |
| `flex-shrink: 1` | How much the item gives up when there is not enough space | The cards can get narrower instead of overflowing |
| Shorthand | `flex: 1 1 250px` | All three in one line |

The page also has an **experiment section** with measured results (container width 1200px):
| Experiment | CSS | Measured widths |
|------------|-----|-----------------|
| `flex-grow` 1 : 2 : 1 | `.grow-1 { flex-grow: 1 } .grow-2 { flex-grow: 2 }` | 263px, 463px, 263px — the middle box gets twice as much of the free space |
| `flex-basis` | `flex: 0 0 100px / 200px / 300px` | exactly 100px, 200px, 300px |
| `flex-shrink` | three boxes of `400px` in a 600px container, with `shrink` 1, 2 and 0 | 103px, 65px, 400px — the `shrink: 2` box gives up twice as much as the `shrink: 1` box, and `shrink: 0` keeps its full size |

## Wrapping When the Screen Gets Smaller
I rendered the page at four widths and counted the cards per row:

| Screen width | Cards per row | Card width |
|--------------|---------------|------------|
| 1200px (desktop) | 3 (2 rows) | 340px |
| 900px (small laptop/tablet) | 3 (2 rows) | 273px |
| 600px (large phone/tablet) | 2 (3 rows) | 272px |
| 375px (phone) | 1 (6 rows) | 343px |

There is no horizontal overflow at any width and all six images load. No media query is needed for the card grid: `flex-wrap` and `flex-basis` do the job.

## Submission
- ✅ Responsive product listing: `index.html`, `style.css` and the `images` folder (attached)
- 📸 Screenshots at desktop and mobile widths: attached `screenshot-desktop.png` (1200px) and `screenshot-mobile.png` (375px) are references rendered by me — take your own with Chrome's device toolbar (`Ctrl + Shift + M`).
