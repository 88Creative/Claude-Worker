# Webflow comparison table

A reusable, on-brand table for side-by-side comparisons in Webflow CMS articles.

- Header row: brand blue `#034F87` with white text
- Body text: `#1A2D3D`
- Borders: `#B3B9BE`
- Alternating light-blue rows, rounded corners, fits phone screens (scrolls sideways only if a single word is too long)

| File | Who uses it | What it is |
| --- | --- | --- |
| `1-site-head-code.html` | Site admin, **once** | The styles. Controls how every table looks. |
| `2-snippet-2-column.html` | Editors | Copy/paste template: Option A vs Option B |
| `3-snippet-3-column.html` | Editors | Copy/paste template: row label + Option A + Option B |
| `preview.html` | Anyone | Open in a browser to see both tables with example content |

---

## One-time setup (site admin)

1. In Webflow, open **Site settings → Custom code**.
2. Paste the entire contents of `1-site-head-code.html` into **Head code**.
3. Save and **Publish** the site.

That's it. To change the look of every table later (colours, spacing), edit
this one block — articles never need to be touched.

> Custom code only renders on the published site or in Preview mode, not in the
> Designer/Editor canvas. In the editor the embed shows as a grey placeholder — that's normal.

---

## Adding a table to an article (editors)

1. Open the article in the CMS and click into the rich text field where the table should go.
2. On a new empty line, click the **+** icon and choose **Embed** (`</>`).
3. Paste the contents of `2-snippet-2-column.html` or `3-snippet-3-column.html`.
4. Replace the placeholder text (see below), then click **Save & Close**.
5. Publish the item and check it on the live page.

### Which one?

- **2 columns** — two things compared directly, e.g. *Renting | Buying* with a list of points under each.
- **3 columns** — a list of features compared across two options, e.g. *Feature | Starter | Pro*.
  The first column is the row label (bold, shaded).

### Editing rules — only change the words

| To change… | Edit the text between… |
| --- | --- |
| Table title | `<caption>` and `</caption>` — or delete that whole line for no title |
| Column headings | `<th scope="col">` and `</th>` |
| Row label (3-col only) | `<th scope="row">` and `</th>` |
| A cell | `<td>` and `</td>` |

**Add a row:** copy one full block from `<tr>` down to its matching `</tr>` and paste it
directly underneath. **Remove a row:** delete one full `<tr> … </tr>` block.

Every row must have the same number of cells as the heading row (2 or 3).

### Do / don't

- ✅ Do change only the words between tags.
- ✅ Do use `<strong>bold</strong>` or `<br>` (line break) inside a cell if needed.
- ✅ Special characters: write `&amp;` for `&`, and `&lt;` for `<`.
- ❌ Don't add `style="…"`, colours or fonts — the design is controlled centrally.
- ❌ Don't delete the `<div class="cmp-table…">` wrapper or the closing `</div>`.

### Optional: ticks and crosses

```html
<td><span class="cmp-yes">✓</span> Included</td>
<td><span class="cmp-no">✗</span> Not included</td>
```

Always keep a word next to the symbol so the meaning doesn't rely on colour alone.
