# Size chart section for Shopify Horizon

This adds a **Size chart** section to your Horizon theme. The section shows a link with zero top and bottom padding. Clicking the link opens your size chart image in a modal that fits both desktop and mobile screens.

Every product uses the same chart image. You set it once in **Theme settings → Size chart**.

| File | Where it goes in your theme |
| --- | --- |
| [`sections/size-chart.liquid`](sections/size-chart.liquid) | `sections/size-chart.liquid` (new file) |
| [`theme-settings-size-chart.json`](theme-settings-size-chart.json) | Paste into `config/settings_schema.json` |

## Install

### 1. Add the chart settings to Theme settings

1. In Shopify admin, go to **Online Store → Themes**. On your Horizon theme, click **⋯ → Edit code**.
2. Open `config/settings_schema.json`. The file is one big list: it starts with `[` and ends with `]`.
3. Scroll to the very end. After the last `}` and before the final `]`, type a comma (`,`), then paste the contents of `theme-settings-size-chart.json`. The end of the file should look like this:

   ```json
     ...
     },
     {
       "name": "Size chart",
       "settings": [ ... ]
     }
   ]
   ```

4. Click **Save**. If Shopify shows a JSON error, the comma is usually missing or doubled.

### 2. Add the section

1. Still in the code editor, in the **sections** folder, click **Add a new section** and name it `size-chart`.
2. Replace its contents with `sections/size-chart.liquid`, then click **Save**.

### 3. Set the chart and place the link

1. Click **Customize**. Open **Theme settings** (the gear icon), go to **Size chart**, and upload your chart image. You can also add an optional mobile image.
2. Open a **product** template. Click **Add section → Size chart** and drag it where you want the link, for example directly under the product information section.
3. Click **Save**. Because this is the product template, the link appears on every product that uses it.

## Settings

**Theme settings → Size chart** (shared by all products):

| Setting | What it does |
| --- | --- |
| Size chart image | The chart shown in the modal. The link is hidden until an image is set. |
| Mobile image (optional) | A separate image for screens under 750px, such as a taller version of a wide chart. |
| Modal heading | Title at the top of the modal. Leave it empty to hide it. |
| Modal max width (desktop) | Maximum width of the modal on desktop, from 400 to 1400px. On mobile it always fills the screen width minus 8px on each side. |

**Size chart section** (per template): link text, ruler icon, underline, font size, text color, alignment, and width (page width or full width).

## Behaviour

- **Link spacing:** the link and its section wrapper have zero top and bottom padding and margin, and the section overrides Horizon's button styling so no extra height is added.
- **Extra space:** if you still see space above or below the link, it comes from the bottom padding of the section next to it, such as Product information. You can reduce that padding in that section's own settings.
- **Section position:** a section sits between other sections. It can't go inside the product information column, for example next to the variant picker.
- **Closing the modal:** it uses the native `<dialog>` element and closes with the X button, the Esc key, or a click on the dark backdrop. Focus returns to the link afterwards.
- **Scrolling:** the page behind the modal is locked. If the chart is taller than the screen, it scrolls inside the modal.
- **Image loading:** the image is lazy-loaded and starts loading when the shopper hovers over or focuses the link.
- **Theme editor:** when you select the section in the editor, the modal opens so you can preview the chart.
